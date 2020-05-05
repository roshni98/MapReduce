

How to run the project:
hadoop jar redditCount.jar redditCount <path_to_input_file_in_hdfs> <path_to_output_folder_in_hdfs>
hadoop fs -get <path_to_output_folder_in_hdfs>

See Result Counts in:

For small file counts:
./smallRedditFileMapReduce

For large file counts:
./largeRedditFileMapReduce

I used a StringTokenizer and read each file line by line, splitting each line with tab. Then in the map operation took the second token (#image_id) as the key and for tokens 3-5 I summed up the upvotes, downvotes, and comments by using Integer.parseInt to calculate the Impact score. Finally in the reduce operation I just summed up all the impact scores for each key. One of the challenges I ran into was working with the iterator. I intially made the mistake of forgetting to move the iterator forward for tokens I was not interested in like unixtime and title. After fixing this, I was able to easily get the results. 

