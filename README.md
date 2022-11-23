# Hadoop
Word Count Map Reduce Code Java

Hadoop Commands:

hadoop fs -mkdir InputFolder                                      //to create a new input folder
hadoop fs -copyFromLocal <input file> InputFolder                  //to copy a file from local directory to hadoop environment
hadoop fs -ls InputFolder                                          //to see the files inside "InputFolder"
hadoop jar <jar file name> <class name> InputFolder OutputFolder   //running mapreduce operation
hadoop fs -ls OutputFolder                                        //to see the files inside "OutputFolder"
hadoop fs -cat OutputFolder/part-r-00000                          //to see the content inside "OutputFolder/part-r-00000" file
hadoop fs -rm -r OutputFolder                                     //to remove "OutputFolder" directory and all its files
remove OutputFolder before generating the next results.
remove/clean InputFolder if you want to use a different file as input.
Common Errors:

Error 1: mkdir: Call From cs6304-akkcm-02/127.0.1.1 to localhost:9000 failed on connection exception: java.net.ConnectException: Connection refused
Explanation and Fix: In general this error comes if you are running hadoop first time on your VM after a reset. The below commands will fix it.

stop-all.sh
hadoop namenode -format
start-all.sh
You can use the below command to check if namenode, datanode and nodemanager are running.

jps

Error 2: mkdir: `hdfs://localhost:9000/user/': No such file or directory
Explanation and Fix: The error comes when there is no directory /user and /user/ in hdfs and you are trying to create a folder using "hadoop fs -mkdir InputFolder ".
Below command will create the directory structure if required and solves the problem.

hdfs dfs -mkdir -p InputFolder
Warning 1: WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Fix: You can just ignore this warning.
