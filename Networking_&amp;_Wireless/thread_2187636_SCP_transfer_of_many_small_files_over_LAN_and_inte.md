---
title: "SCP transfer of many small files over LAN and internet"
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by erotavlas on 2013-11-13
Hi all,
 
I have to continually transfer about 10-20 files (each about 10 kbyte to a maximum of 1 Mbyte) from two servers over LAN or over internet. The scenario is the following: the server A produces a set of files and the server B reads these files. The production and reading phases are independents since that each file has it own sequence number. Each time that the server B has completed to read a group of files, it passes to the following group. I need authentication and encryption. At the moment I'm using scp combined with different option for encryption and compression: 
 
```

scp -c arcfour (blowfish) -C your_username@rh1.edu:/some/remote/directory/foobar.txt your_username@rh2.edu:/some/remote/directory/ 

```  

My question are: 1) by combining the 10-20 scp command in unique command, can I speed the transfer? 2) I read that the sftp is not good alternatives for small files. 3) This project [http://www.psc.edu/index.php/hpn-ssh](http://www.psc.edu/index.php/hpn-ssh) appears actractive. Have you tried it?

Any suggestions is welcome.
Thank you

---

### Post by Lars Noodén on 2013-11-13
Where did you read that sftp was not good for small files?  I would think that especially in batch mode (-b) using a key, it would be quite efficient.  

Otherwise, if you are going to use scp instead and are calling it 10 - 20 times, you might look into [multiplexing](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Multiplexing).  The master connection  will be normal speed, but then all the subsequent connections reusing that master are much faster.

However, short of new information or multiplexing, I would figure sftp the better one.

---

### Post by erotavlas on 2013-11-13
Here I read that scp is faster than sftp [http://superuser.com/questions/134901/whats-the-difference-between-scp-and-sftp](http://superuser.com/questions/134901/whats-the-difference-between-scp-and-sftp). But here [http://laurentschneider.com/wordpress/2011/05/scp-tuning.html](http://laurentschneider.com/wordpress/2011/05/scp-tuning.html) the author show the converse but it is transferring an huge file. I have read your link about multiplexing. In the case of scp, what is better to do one scp command and transfer all set of files or to use multiplexing and open one master connection and several sub connections one for each file?
In the case of sftp, what is the answer to the previous question?

What do you suggest to achieve the fastest solution?

Thank you

---

### Post by Lars Noodén on 2013-11-13
Thanks for the links.  I'm going to have to look further into that and see what else is written about performance.  

About one or many SCP connections, it looks like the fastest option may be to just use one scp connection.

```

scp ./* server.example.org:/some/path/.

```

I wish I knew more about how the connections work, then it would be easy to predict the fastest method.  Specifically, if scp uses one tcp connection, then there is no real advantage of multiplexing.  I've done some time trials but not enough to deduce what is going on behind the scenes.  But it did look like SFTP was slower by a small amount in proportion to the amount transfered.  You can do some time trials with your actual data set and see how much is actually used.

```

time scp ./* server.example.org:/some/path/.

```

Then do the same for sftp in batch mode.

```

time sftp -b upload.batch server.example.org:/some/path/

```

For batch mode, you'll need to use a key.

---

### Post by Lars Noodén on 2013-11-13
If the files don't change completely, then I would use rsync instead.  That only transfers the changes so if the files are mostly unchanged, it will be much, much faster than scp or sftp.  It works over ssh and can be configured to use keys.

---

### Post by Lars Noodén on 2013-11-13
Whichever method you use, it will be faster by upgrading to the blowfish cipher.  Here is an example copying 32 x 1MB files:
 
```

	real	user	sys	
sftp batch				
	16.332	0.442	0.333	
	16.495	0.457	0.354	
	16.926	0.434	0.338	
	16.584	0.444	0.342	avg
sftp blowfish				
	11.541	1.409	0.313	
	11.090	1.436	0.324	
	10.824	1.443	0.326	
	11.152	1.429	0.321	avg
scp blowfish				
	9.214	1.232	0.211	
	9.962	1.007	0.157	
	11.084	1.283	0.209	
	10.087	1.174	0.192	avg
scp plain				
	15.865	0.386	0.234	
	15.765	0.370	0.227	
	15.277	0.369	0.224	
	15.636	0.375	0.228	avg

```

[s]So far, ssh still defaults to 3DES[/s].  So you have to specify blowfish manually or else add it to ~/.ssh/config.

---

### Post by erotavlas on 2013-11-13
Hi,

have you read my first post? I have tried with blowfish and arcfour but it seems to make no difference. Now I'm trying to make one single scp with all files instead of one scp of each file with multiplexing. I don't know where is the problem, actually I'm programming in Java and I'm using jsch library [http://www.jcraft.com/jsch/examples/](http://www.jcraft.com/jsch/examples/). 
Thank you for your example.

---

### Post by SeijiSensei on 2013-11-13
> **Lars Noodén said:**
> If the files don't change completely, then I would use rsync instead.  That only transfers the changes so if the files are mostly unchanged, it will be much, much faster than scp or sftp.  It works over ssh and can be configured to use keys.

Another vote for rsync, even if the files do change completely.  Have you given it a try yet, erotavlas?

Another option is to run a script that creates a compressed tarball of the files, ships the tarball via scp, then runs a command on the remote via ssh to unpack the files.

Yet another route is to use OpenVPN to set up an [encrypted tunnel]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") between the two machines and use NFS over the tunnel to mount a directory on the source machine on the remote.

---

### Post by Lars Noodén on 2013-11-13
> **erotavlas said:**
> ...actually I'm programming in Java and I'm using jsch library [http://www.jcraft.com/jsch/examples/](http://www.jcraft.com/jsch/examples/).

Then this might not be an ssh/scp/sftp question at all and might be a JSch question. ;)  From the web page, it appears to be an independent implementation of SSH2 and not interact with the regular OpenSSH tools at all.  So, you might post this over in the programming section to get input from java users and help with that module.

---

### Post by erotavlas on 2013-11-14
> **Lars Noodén said:**
> Then this might not be an ssh/scp/sftp question at all and might be a JSch question. ;)  From the web page, it appears to be an independent implementation of SSH2 and not interact with the regular OpenSSH tools at all.  So, you might post this over in the programming section to get input from java users and help with that module.

You are right but before to proceed with programming I need to know what is the best solution. I made this bash script and I discover that there is no difference between with scp: in particular sending 10 files by using 10 scp commands in parallel and 1 single command with 10 files require the same time. Now I'm trying to the same thing with sftp.

[Updates]
In my case it seems that there is no differences between scp and sftp. You can try the script.

Thank you

```

#!/bin/bash

USER="foo"
REMOTE_PATH="/home/foo/"
REMOTE_IP="10.1.2.78"
PORT="22"
LOCAL_PATH="/home/foo/"
LOCAL_DATA=$LOCAL_PATH"Desktop/provaSCP/"
CIPHER=arcfour #blowfish
BATCH_FILE="batch_file"

# do only one time
printf "ssh -fN -o \"ControlMaster=yes\" -o \"ControlPersist=yes\" -o \"ControlPath=$LOCAL_PATH.ssh/$USER@$REMOTE_IP:$PORT\"  $USER@$REMOTE_IP"
ssh -fN -o "ControlMaster=yes" -o "ControlPersist=yes" -o "ControlPath=$LOCAL_PATH.ssh/$USER"@"$REMOTE_IP:$PORT"  $USER@$REMOTE_IP

####################### scp each file
STARTTIME="$(date +%s%N)"
# loop over files
for file in $LOCAL_DATA* 
do
    #printf "scp -o \"ControlPath=$LOCAL_PATH.ssh/$USER@$REMOTE_IP:$PORT\" -c $CIPHER -C $file $USER@$REMOTE_IP:$REMOTE_PATH &\n"
    scp -o "ControlPath=$LOCAL_PATH.ssh/$USER@$REMOTE_IP:$PORT" -c blowfish -C $file $USER@$REMOTE_IP:$REMOTE_PATH &
done
wait
ENDTIME="$(date +%s%N)"
printf "One scp for each file takes $((($ENDTIME - $STARTTIME)/1000000000)) seconds\n\n"

############################ scp all file
# loop over files
files=""
for file in $LOCAL_DATA* 
do 
    #printf "$file"
    files=$files" $file "
done
STARTTIME="$(date +%s%N)"
#printf "scp -o \"ControlPath=$LOCAL_PATH.ssh/$USER@$REMOTE_IP:$PORT\" -c $CIPHER -C $files $USER@$REMOTE_IP:$REMOTE_PATH"
scp -o "ControlPath=$LOCAL_PATH.ssh/$USER@$REMOTE_IP:$PORT" -c blowfish -C $files $USER@$REMOTE_IP:$REMOTE_PATH
ENDTIME="$(date +%s%N)"
printf "One scp for all files takes $((($ENDTIME - $STARTTIME)/1000000000)) seconds\n\n"

############################ sftp all file
# delete file
rm -f $BATCH_FILE
echo "put "$LOCAL_DATA* >> $BATCH_FILE

STARTTIME="$(date +%s%N)"
printf "sftp -o \"ControlPath=$LOCAL_PATH.ssh/$USER@$REMOTE_IP:$PORT\" -c $CIPHER -C -b $BATCH_FILE -P $PORT $REMOTE_IP:$REMOTE_PATH"
sftp -o "ControlPath=$LOCAL_PATH.ssh/$USER@$REMOTE_IP:$PORT" -c $CIPHER -C -b $BATCH_FILE -P $PORT $REMOTE_IP:$REMOTE_PATH
ENDTIME="$(date +%s%N)"
printf "One sftp for all files takes $((($ENDTIME - $STARTTIME)/1000000000)) seconds\n"

```

---

### Post by Lars Noodén on 2013-11-14
In multiplexing, the controlmaster has to stay open all the time.  In the script you should use ssh(1) to create the controlmaster.  If you use scp(1), the master connection goes away when that instance of scp(1) completes, unless you have found some way to keep it open.   Also, with ssh(1), you'll need something to keep the connection open for the duration that scp(1) is going to be using it such as -fN.  That will cause it to drop to the background, you can find it again with pgrep or ps.  

```

# do only one time
ssh -fN -o "ControlMaster=yes" -o "ControlPersist=yes" -o "ControlPath=$LOCAL_PATH.ssh/$USER"@"$REMOTE_IP:$PORT"  $USER@$REMOTE_IP

```

With the -b option in sftp(1), just include what you would have typed.  I've tried both literal filenames and globbing and both seem to work for me.

---

### Post by Lars Noodén on 2013-11-14
In the instances of scp(1) where you wish to not use multiplexing, then it should probably not refer to ControlPath.  

Also, in the batch mode for sftp(1), the option -b points to a file where you have your gets or puts or cds and so on.  It should contain exactly what you would have otherwise typed when using it manually.

```

cd /home/pippo/uploads
put 01.txt
put 02.txt

```

---

### Post by erotavlas on 2013-11-14
> **Lars Noodén said:**
> In the instances of scp(1) where you wish to not use multiplexing, then it should probably not refer to ControlPath.  

Also, in the batch mode for sftp(1), the option -b points to a file where you have your gets or puts or cds and so on.  It should contain exactly what you would have otherwise typed when using it manually.

```

cd /home/pippo/uploads
put 01.txt
put 02.txt

```

Ok, I have corrected the previous post with good one. There is no difference between scp and sftp using or not multiplexing. Check it in your test case.
Best Regards

---

### Post by Lars Noodén on 2013-11-14
I tried some method of copying 64 x 1024KB files to a remote RAM disk.

```

ssh -M -S /tmp/mux -fN xx.yy.zz.aa

time sftp -b 0xxxxx xx.yy.zz.aa:.
time sftp -b 0xxxxx xx.yy.zz.aa:.

time sftp -o "ControlPath=/tmp/mux" -b 0xxxxx xx.yy.zz.aa:. 
time sftp -o "ControlPath=/tmp/mux" -b 0xxxxx xx.yy.zz.aa:. 

scp -o "ControlPath=/tmp/mux" ./?? xx.yy.zz.aa:.
scp -o "ControlPath=/tmp/mux" ./?? xx.yy.zz.aa:.

time scp ./?? xx.yy.zz.aa:.
time scp ./?? xx.yy.zz.aa:.

time (for i in ??;do scp $i xx.yy.zz.aa:.;done)
time (for i in ??;do scp $i xx.yy.zz.aa:.;done)

[s]time (for i in ??;do scp -o "ControlPath=/tmp/mux" $i xx.yy.zz.aa.;done)[/s]
[s]time (for i in ??;do scp -o "ControlPath=/tmp/mux" $i xx.yy.zz.aa.;done)[/s]
time (for i in ??;do scp -o "ControlPath=/tmp/mux" $i xx.yy.zz.aa:.;done)
time (for i in ??;do scp -o "ControlPath=/tmp/mux" $i xx.yy.zz.aa:.;done)

ssh -S /tmp/mux -O check true
ssh -S /tmp/mux -O exit true

```

I get a small difference between sftp and scp.   The multiplexing only really helps in the last case, with independent scps, where a lot of new connections would otherwise be made.  Things being more or less equal, I'd go with sftp based on what I've read about it, if rsync is not an option.  

Here are the times from the above commands:

sftp batch

real	0m32.232s
user	0m0.898s
sys	0m0.710s

real	0m31.479s
user	0m0.855s
sys	0m0.689s


sftp multiplex

real	0m30.754s
user	0m0.091s
sys	0m0.222s

real	0m31.026s
user	0m0.093s
sys	0m0.227s


scp globbng multiplex

real	0m29.697s
user	0m0.037s
sys	0m0.144s

real	0m29.441s
user	0m0.759s
sys	0m0.485s


scp globbing

real	0m29.067s
user	0m0.761s
sys	0m0.476s

real	0m29.380s
user	0m0.756s
sys	0m0.466s


scp standalone

real	1m7.930s
user	0m2.050s
sys	0m1.329s

real	1m6.792s
user	0m2.097s
sys	0m1.336s


scp standalone multiplex

real	0m33.199s
user	0m0.617s
sys	0m0.616s

real	0m33.361s
user	0m0.648s
sys	0m0.624s

---

### Post by erotavlas on 2013-11-15
> **Lars Noodén said:**
> I tried some method of copying 64 x 1024KB files to a remote RAM disk.

```

ssh -M -S /tmp/mux -fN xx.yy.zz.aa

time sftp -b 0xxxxx xx.yy.zz.aa:.
time sftp -b 0xxxxx xx.yy.zz.aa:.

time sftp -o "ControlPath=/tmp/mux" -b 0xxxxx xx.yy.zz.aa:. 
time sftp -o "ControlPath=/tmp/mux" -b 0xxxxx xx.yy.zz.aa:. 

scp -o "ControlPath=/tmp/mux" ./?? xx.yy.zz.aa:.
scp -o "ControlPath=/tmp/mux" ./?? xx.yy.zz.aa:.

time scp ./?? xx.yy.zz.aa:.
time scp ./?? xx.yy.zz.aa:.

time (for i in ??;do scp $i xx.yy.zz.aa:.;done)
time (for i in ??;do scp $i xx.yy.zz.aa:.;done)

time (for i in ??;do scp -o "ControlPath=/tmp/mux" $i xx.yy.zz.aa.;done)
time (for i in ??;do scp -o "ControlPath=/tmp/mux" $i xx.yy.zz.aa.;done)

ssh -S /tmp/mux -O check true
ssh -S /tmp/mux -O exit true

```

I get a small difference between sftp and scp.   The multiplexing only really helps in the last case, with independent scps, where a lot of new connections would otherwise be made.  Things being more or less equal, I'd go with sftp based on what I've read about it, if rsync is not an option.  

Here are the times from the above commands:

sftp batch

real    0m32.232s
user    0m0.898s
sys    0m0.710s

real    0m31.479s
user    0m0.855s
sys    0m0.689s


sftp multiplex

real    0m30.754s
user    0m0.091s
sys    0m0.222s

real    0m31.026s
user    0m0.093s
sys    0m0.227s


scp globbng multiplex

real    0m29.697s
user    0m0.037s
sys    0m0.144s

real    0m29.441s
user    0m0.759s
sys    0m0.485s


scp globbing

real    0m29.067s
user    0m0.761s
sys    0m0.476s

real    0m29.380s
user    0m0.756s
sys    0m0.466s


scp standalone

real    1m7.930s
user    0m2.050s
sys    0m1.329s

real    1m6.792s
user    0m2.097s
sys    0m1.336s


scp standalone multiplex

real    0m33.199s
user    0m0.617s
sys    0m0.616s

real    0m33.361s
user    0m0.648s
sys    0m0.624s

Ok thank you for your trials. My results are in disagree with yours. In particular if I use a parallel transfer, the scp outperforms the sftp. Do you confirm this?
```


time (for i in ??;do scp -o "ControlPath=/tmp/mux" $i xx.yy.zz.aa. &;done wait)
time (for i in ??;do scp -o "ControlPath=/tmp/mux" $i xx.yy.zz.aa. &;done wait )

```

---

### Post by Lars Noodén on 2013-11-15
I'll give it a try, when I get at the same equipment again.

---

### Post by erotavlas on 2013-11-15
What about using sshfs? I found this interesting test [http://www.damtp.cam.ac.uk/user/ejb48/sshspeedtests.html](http://www.damtp.cam.ac.uk/user/ejb48/sshspeedtests.html)

---

### Post by Lars Noodén on 2013-11-15
sshfs should work, too, but it is based on SFTP.  So my guess would be that it would be a tad slower than SFTP.

What about compression?  Depending on several factors such as CPU adding compression will make the transfer faster or slower.  The option to add compression is -C in all three utilities, ssh, scp and sftp.

---

### Post by Lars Noodén on 2013-11-15
Sorry for the delay.

> **erotavlas said:**
> Ok thank you for your trials. My results are in disagree with yours. In particular if I use a parallel transfer, the scp outperforms the sftp. Do you confirm this?
```


time (for i in ??;do scp -o "ControlPath=/tmp/mux" $i xx.yy.zz.aa. &;done wait)
time (for i in ??;do scp -o "ControlPath=/tmp/mux" $i xx.yy.zz.aa. &;done wait )

```

For launching scp concurrently using &, I get an error and the files never all transfered.  Sometimes very few of the files actually transfered.  In some cases only 2 out of 64.  The errors were "exec request failed on channel *n*	and "lost connection".  So that method is potentially very unreliable.

For three other uses of scp, I get the following just to check again (I didn't bother with compression because I know from past experiments that the processor on the target is too weak and slows things down.)  I should try larger and smaller files, too.  But it looks like the controlling factors are TCP connection startup and SSH connection startup.  

time (for i in ??;do scp $i xx.yy.zz.aa:.;done)				
```

scp standalone				
	real	user	sys	
	67.839	2.044	1.304	
	66.020	2.074	1.302	
	65.198	2.046	1.279	
	65.371	2.085	1.313	
	65.289	2.075	1.312	
	65.943	2.065	1.302	avg

```
												
time (for i in ??;do scp -o "ControlPath=/tmp/mux" "$i" xx.yy.zz.aa:.;done)				
```

scp standalone multiplex				
	real	user	sys	
	33.387	0.628	0.606	
	32.802	0.623	0.605	
	32.875	0.634	0.615	
	32.816	0.641	0.595	
	32.807	0.628	0.602	
	32.937	0.631	0.605	avg

```				
				
time (scp ?? xx.yy.zz.aa:.)				
```

scp globbing				
	real	user	sys	
	28.566	0.727	0.425	
	28.555	0.746	0.440	
	28.536	0.712	0.418	
	28.625	0.712	0.417	
	28.531	0.725	0.426	
	28.563	0.724	0.425	avg

```

time sftp -b 0xxxx xx.yy.zz.aa:.				
```

sftp batch				
	30.648	0.838	0.626	
	31.856	0.850	0.631	
	30.610	0.820	0.600	
	30.771	0.840	0.635	
	30.656	0.876	0.651	
	30.908	0.845	0.629	avg

```
				
time sftp -o "ControlPath=/tmp/mux" -b 0xxxx xx.yy.zz.aa:.				
```

sftp batch multiplex				
	30.082	0.880	0.219	
	30.064	0.086	0.212	
	30.094	0.085	0.210	
	30.125	0.087	0.212	
	30.082	0.088	0.212	
	30.089	0.245	0.213	avg

```

---

### Post by Lars Noodén on 2013-11-17
I did some more experiments with measuring transfer speeds:

[http://people.ubuntu.com/~larsnooden/sftp-v-scp-speeds.ods](http://people.ubuntu.com/~larsnooden/sftp-v-scp-speeds.ods)

It looks like for small files sftp is the fastest, though in absolute terms the difference is small.  I used the defaults for ciphers and buffers.  One thing that might speed up the transfer more might be if the buffer was set to just over the file size of your files.  

For larger sets, I started to get inconsistent times for scp but that's not so relevant to the 10 - 20 files of 10KB to 1MB in size.

---

### Post by erotavlas on 2013-11-18
Thank you very much for your availability.

---

