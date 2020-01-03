# 101 Hadoop and HDFS

Module 1, Big Data course (81932), University of Bologna.

## 101-1 Cluster setup

Goal: setup connections to the classroom's cluster via Putty and WinSCOP

- Create a connection to isi-vclust**N**.csr.unibo.it on Putty
  - **N** is the number of the node you have been assigned to
- Get your credentials from https://tinyurl.com/bigdata20users 
- Change your password!
```passwd <username>```
- Create a directory in your home called bigdata
```mkdir <foldername>```
- Connect to isi-vclustN.csr.unibo.it via WinSCP
- Check the existence of the directory

## 101-2 HDFS disk usage

Goal: understand basic HDFS commands that provide reports on the disk usage

```
hdfs dfs -df -h
hdfs dfs -du -h /
hdfs dfsadmin -report
```

## 101-3 HDFS storing files

Goal: create/remove files and directories; navigate directories; change the replication factor of files.

### From shell

```shell
# Explore HDFS directories with –ls
hdfs dfs -ls /
# Create a bigdata folder in your HDFS home
hdfs dfs -mkdir bigdata
# Create a dummy file in your folder in the local file system
echo 'This is a dummy file' > dummy.txt
# Put the dummy file to your bigdata folder in HDFS
hdfs dfs -put bigdata/dummy.txt
# Change the replication factor of the dummy file to 5
hdfs dfs -setrep -w 5 bigdata/dummy.txt
# Verify that the number of replicas has actually increased
# Delete the test folder and the dummy.txt file on HDFS
hdfs dfs –rm -skipTrash bigdata/dummy.txt
```

### From HDFS's web UI

HDFS provides a basic web interface with read permissions on the filesystem. 

Go to [Cloudera Manager](http://137.204.72.233:7180/cmf/home) (Username: student - Password: student) > HDFS service (left panel) > NameNome Web UI > Utilities > Browse the file system. Navigate to your folder and click on your file to check blocks' locations and download the file.

### From Apache Hue

Apache Hue offers a more complete navigation of the filesystem, with the possibility to create/move/rename/delete folders and files. You can change permissions, download files, and use the drag&drop feature to easily upload new files and folders.

Go to [Apache Hue](http://137.204.72.233:8888) and click on the three-lines menu (top-left) > Files.
