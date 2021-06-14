# Data analytics with pyspark
## Setting things up
First create an AWS EMR cluster. Select Spark application as analytics engine from the settings. Select your necessary instance type and put total number of instance to create. There will be one Master and some slave instances. This process needs an EC3 key pair. Put an existing EC2 key pair or create a new one and select the file from respective menu. It can take 5-10 minutes for an EMR cluster to activate. It will show 'Waiting'- status once activated.

Turn on the ssh port from the security group of the master node. Just navigate to `Security group for master` and select `Edit inbound rules > Add rules`. Then select ssh and allow all source or your machine IP in the `Source` column.

## Dataset download
Download the stackoverflow annual developer survay from [here](https://insights.stackoverflow.com/survey)
upload the csv file to amazon S3 Bucket and link the S3 uri in the python script. Upload the python script in the same S3 Bucket. In our case the python file name is `pyspark-stackoverflow.py`

## Analyze the data
To analyze the data- first, ssh to the spark emr instance. The ssh command is available in the `Connect to the Master Node Using SSH` option. Select your operating system and run the ssh command accordingly. This process requires the key pair given while the setup of the EMR instance.

Then copy the python file inside your cluster from the S3 bucket using the command-

`aws s3 cp s3://<bucket_name>/<py_file_name.py> .`

Then run the analytics using the command-
`spark-submit <py_file_name.py>`

## Result
![](https://i.ibb.co/GkcjbtX/result-1-png.png)
*(This screenshot is one of the few analytics)*