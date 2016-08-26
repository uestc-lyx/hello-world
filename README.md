# hello-world
My first repository

about me: a student, studying on android and hadoop

1.hadoop :
public static class Map extends Mapper<Object, Text, IntWritable, Text> {                 
		public void map(Object key, Text value, Context context) throws IOException, InterruptedException {
		}		
		}

public static class Reduce extends Reducer<Text, Text, Text, Text> {
		public void reduce (Text key, Text values, Context context) throws IOException, InterruptedException {

	  }
	  }
public void Mapreduce() throws Exception {
      Configuration conf = new Configuration();
			conf.set("fs.default.name", "hdfs://:9000");
			String[] ioArgs = new String[] {"/", "/"};
			String[] otherArgs = new GenericOptionsParser(conf, ioArgs).getRemainingArgs();		
			if(otherArgs.length !=2) {
				System.err.println("readtif <in> <out>");
				System.exit(2);
			}		
			Job job = new Job(conf, "mrreadtifputtxt");
			job.setJarByClass(mrreadtifputtxt.class);		
			job.setMapperClass(Map.class);
			job.setReducerClass(Reduce.class);
			job.setMapOutputKeyClass(IntWritable.class);
			job.setMapOutputValueClass(Text.class);
			job.setOutputKeyClass(IntWritable.class);
			job.setOutputValueClass(Text.class);		
			FileInputFormat.addInputPath(job, new Path(otherArgs[0]));
			FileOutputFormat.setOutputPath(job,  new Path(otherArgs[1]));
			if (job.waitForCompletion(true)) {
				System.out.println("MapReduce completed！");
				System.exit(0);
			}
  }
public static void main(String[] args) throws Exception {	
    	mrreadtifputtxt rtf = new mrreadtifputtxt();
		  rtf.Mapreduce();
	}
