---
title: "run python script remotely on local files"
date: 2015-11-04
forum: Networking &amp; Wireless
---

### Post by cybermecano on 2015-11-04
Hi,

I am wondering if I could transfer a python script to a remote machine then use the computing resources of that machine to run the python script on a local files as input without the need of transferring these files to the remote machine. The aim is to avoid wasting time in transferring the files (both the input and the output ones) since they are quite big and also to avoid managing the storage space in the remote machine (I am asked to free the working space in the remote machine a.s.a.p.). To be clear, the python script used to be run locally as follow:
```
me@local_machine:/$ python my_script.py 'path/to/local/input/directory'
```
I found couple of ways to run local python script using remote machine:
```
me@local_machine:/$ cat my_script.py | ssh me@remote_machine.com python -  
```
or
```
me@local_machine:/$ ssh me@remote_machine.com python < ./my_script.py
```
so, how to pass my **local input path** as argument to my python script (no matter where it is located)? Do you think this will work:
```
me@local_machine:/$ ssh me@remote_machine.com python /remote/path/my_script.py < '/path/to/local/input/directory'
```
Thanks a lot.

A.

---

### Post by ian-weisser on 2015-11-04
The python script and the data exist in two entirely different filesystems. You can't easily operate on two unrelated fiesystems in an easy one-line shell command.

One solution is to keep the filesystems separate and scp the python script to the remote machine. Then ssh and run the script-and-data entirely remotely.
Another solution is to mount the remote filesystem onto a branch of the local using, say, sshfs. Then the data is accessable on your local filesystem without copying.

Example of the second method:
```
$ mkdir /tmp/remote_data                        ## Create the mount point
$ sshfs me@remote:/home/data /tmp/remote_data   ## Mount the remote data as a local dir without copying
$ python myscript /tmp/remote_data  > output_file
$ umount /tmp/remote_data                       ## Clean up
```

---

### Post by cybermecano on 2015-11-04
Thank you very much.

I am not sure but I feel that the solution suggested here is relative to data already at the remote machine whereas I am looking for solution in the opposite way, meaning computing remotely on local data. Thus, if I do it the other way will it work, meaning:

```
#go to remote
[me@remote ~/]$ mkdir /tmp/local_data                                          ## Create the mount point **on the remote**

#back to local
me@local:~/$ sshfs /path/to/local/input/directory me@remote:~/tmp/local_data   ## Mount the **local** data as a **remote** dir without copying

#back to remote
[me@remote ~/]$ python my_script.py '/tmp/local_data'                          ## **run remote python script on remotely [B]mounted but still** local data ???[/B]
[me@remote ~/]$ umount /tmp/local_data                                         ## Clean up
```

Am I wrong ?

I look forward to reading your reply!

Many thanks.

> **ian-weisser said:**
> The python script and the data exist in two entirely different filesystems. You can't easily operate on two unrelated fiesystems in an easy one-line shell command.

One solution is to keep the filesystems separate and scp the python script to the remote machine. Then ssh and run the script-and-data entirely remotely.
Another solution is to mount the remote filesystem onto a branch of the local using, say, sshfs. Then the data is accessable on your local filesystem without copying.

Example of the second method:
```
$ mkdir /tmp/remote_data                        ## Create the mount point
$ sshfs me@remote:/home/data /tmp/remote_data   ## Mount the remote data as a local dir without copying
$ python myscript /tmp/remote_data  > output_file
$ umount /tmp/remote_data                       ## Clean up
```

---

### Post by ian-weisser on 2015-11-04
I totally misread your problem. Sorry about that.
You have local python script and local data, but you want to use a remote python interpreter.

Your solution of sshing to remote, then sshfs the local filesystem onto the remote is certainly worth a try. It should work...if you have an ssh server on both machines, and can wrap your brain around the concept. However, since the script and data must all be streamed/copied onto the remote machine anyway, I feel that this complex solution may not be worthwhile.

Instead, perhaps back to the simple step process: Scp the script to remote, scp the data to remote, ssh to run, (optional) scp the output product to local, (optioanl) ssh to cleanup.
A simple bash script wrapper around the python command should do it properly, and scp has lower i/o overhead than sshfs. Easier to debug and possibly faster.

---

