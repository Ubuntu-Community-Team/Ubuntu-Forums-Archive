---
title: "Confusing lines in /var/log/syslog"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Solarium on 2009-02-06
A litte question to you guys, first off i am not sure i have a problem or something, but my logic tells me something is wrong :P
I tryed googling the lines i am getting in more generic form yet i had no luck hope you guys could explain.

I had some errors and wanted to view the system log, when it opened i have this line in /var/log/syslog:
```
Feb  6 22:17:14 cube kernel: [ 6369.852018] eth0: auto-negotiating...
```

The problem is that i get this message every 10 seconds ? whats up with it and what does it mean ? (i am geussing its looking for eth0 ?)

I am using a laptop with wireless connection and dont plan on using ethernet so is it possible to disable this ? ( will it be benificial to do so ?)

Another "problem" is these lines, i get them every 5 seconds:
```
Feb  6 22:24:22 cube nullmailer[4623]: Rescanning queue.
Feb  6 22:24:22 cube nullmailer[4623]: Starting delivery: protocol: smtp host: mail. file: 1230744132.7157
Feb  6 22:24:22 cube nullmailer[21684]: smtp: Failed: Connect failed
Feb  6 22:24:22 cube nullmailer[4623]: Sending failed:  Host not found
Feb  6 22:24:22 cube nullmailer[4623]: Starting delivery: protocol: smtp host: mail. file: 1232192732.6398
Feb  6 22:24:22 cube nullmailer[21685]: smtp: Failed: Connect failed
Feb  6 22:24:22 cube nullmailer[4623]: Sending failed:  Host not found
Feb  6 22:24:22 cube nullmailer[4623]: Starting delivery: protocol: smtp host: mail. file: 1230573961.7777
Feb  6 22:24:22 cube nullmailer[21686]: smtp: Failed: Connect failed
Feb  6 22:24:22 cube nullmailer[4623]: Sending failed:  Host not found
Feb  6 22:24:22 cube nullmailer[4623]: Delivery complete, 3 message(s) remain.
```

My question would be similar as the previous one: what is nullmailer what is it checking for ? and can / should i disable it to "boost" system prefermance ?


Thank you very much for help and education.

---

### Post by blueridgedog on 2009-02-06
If you right click the network icon on the task bar, then select "edit connections" you can then select eth0 under the wired tab, then edit then uncheck "connect automatically".  It may solve your issue.

As far as nullmailer, it is a simple mail exchange tool that will let your system send mail through your ISP approved mail server.  You can configure it by editing the file located at: /etc/nullmailer/remotes

The configuration would look like:

mail.server.com smtp --port=25 --user=me@host --pass=changeme

The first part is your ISP's mail server, then your username and password.  

I do not think it is installed by default, so a something that you have installed my have installed it as a dependency.  The message indicates that it has some mail to send.  If you dont' need it, you can uninstall it.

---

### Post by Solarium on 2009-02-07
Thanks for the reply !

I have tryed doing what you suggested for the eth0 i even removed it from the wired connections tab but i am still the same line every 10 seconds.

Regarding the nullmailer also had no luck, i am currently using only web mail never tryed setting up mail client on this install ... i dont even have evolution installed (i removed it, only thing thats left from it is evolution-data-server-common)
Oh and now it says 4 messages remain even tho i didnt do anything :P

Any other ideas would be appreciated.

---

### Post by blueridgedog on 2009-02-07
Are the messages in /var/spool/mail?  Post the output of 

```
ls /var/spool/mail
```

That was by best swing at eth0, I suggest you ignore it.  Others may have better ideas.

---

### Post by Solarium on 2009-02-07
I see this messages thru the System log, they are displayed in /var/log/syslog (also in all the mail.*)

When did ls /var/spool/mail nothing happened it just jumped back to the $.

---

### Post by blueridgedog on 2009-02-07
Most system mail is stored in /var/spool/mail, and I was thinking that if nullmailer stored mail there, we could simply delete the messages that were pending.  You can try uninstalling nullmailer if it bugs you:
```

apt-get --purge remove nullmailer
```

---

### Post by Solarium on 2009-02-07
Well that commands looks like it did the trick for the mail messages, only when running the command you gave i got this error at the end:
```
Removing nullmailer ...                                                            
 * Stopping mail-transfer-agent:                                                                                                                                             [ OK ] 
Purging configuration files for nullmailer ...                                                                                                                                      
dpkg - warning: while removing nullmailer, directory `/var/spool/nullmailer/queue' not empty so not removed.                                                                        
dpkg - warning: while removing nullmailer, directory `/var/spool/nullmailer' not empty so not removed.                                                                              
Processing triggers for man-db ... 
```

After i tryed accessing the folder and it wont let me saying permission denied @_@ i tryed using sudo and such  but still seems like i am locked out ... this sudo thing makes me feel sometimes like a quest at my own computer and not the owner but i am sure it cause of a little bit lack og knowledge from my side :D

---

### Post by blueridgedog on 2009-02-07
I am sorry, that should have been 

```
sudo apt-get --purge remove nullmailer
```

Did you try that?  

At least we know where the emails are:

```
/var/spool/nullmailer/queue
```

If you can't remove/purge nullmailer, can you post the output of:

```
ls -al /var/spool/nullmailer/queue
```

---

### Post by Solarium on 2009-02-07
Well when i tryed running ```
sudo apt-get --purge remove nullmailer
``` i got the message that it was not installed so it didnt remove anything.
The ```
ls -al /var/spool/nullmailer/queue
``` only worked when i did **sudo** other wise i got permission denied.

```
misha@cube:~$ sudo ls -al /var/spool/nullmailer/queue
total 24
drwxr-x--- 2 mail root 4096 2009-02-07 13:38 .
drwxr-xr-x 3 mail root 4096 2009-02-07 15:54 ..
-rw------- 1 mail root  451 2008-12-29 20:06 1230573961.7777
-rw------- 1 mail root  670 2008-12-31 19:22 1230744132.7157
-rw------- 1 mail root  459 2009-01-17 13:45 1232192732.6398
-rw------- 1 mail root  355 2009-02-07 13:38 1234006693.6769

```

Is there anyway for me to access that **queue** folder ? its getting on my nerves that i can't .... i tryed doing sudo cd /var/spool/nullmailer/queue and i get the message: cd command not found and if i do it without sudo i am getting: permission denied.

EDIT: I stoped getting the mail messages btw so it worked like i said in the priveous post i am just currious on what it was... (in case i wasnt clear)
Thank you very much for sticking with me and helping man !

---

### Post by blueridgedog on 2009-02-07
Well, there are your four messages.  You can see what is in them with:

```
sudo cat /var/spool/nullmailer/queue | more
```

An easy way to get to the location as root would be to run nautilus as as sudo command, 

```
sudo nautilus
```

But I don't recommend it as you could delete something else.  You can do every thing you want from the terminal with sudo in this case.  

It appears that the package is uninstalled.  

Look at the messages using the command I gave you and if you are convinced that they are moot, you can delete them with

```
sudo rm /var/spool/nullmailer/queue/*
```

---

### Post by Solarium on 2009-02-07
Thanks for all the help blueridgedog.

I belive i wont be deleting the files since they look strange to me ... but the error messages stoped and thats all i wanted.

Here is what the messages contain geuss its some system thing some error handling or w/e , here they are:
First ```
root@cube.cube
root@cube.cube

Received: (nullmailer pid 7777 invoked by uid 0);
	Mon, 29 Dec 2008 18:06:01 -0000
From: Anacron <root@cube.cube>
To: root@cube.cube
Subject: Anacron job 'cron.daily' on cube
Date: Mon, 29 Dec 2008 20:06:01 +0200
Message-Id: <1230573961.854031.7776.nullmailer@cube>

/etc/cron.daily/apt:
Checking for new archive signing keys now
gpg: [don't know]: invalid packet (ctb=3c)
gpg: keydb_search_first failed: invalid packet
```

Second:
```
root@cube.cube
root@cube.cube

Received: (nullmailer pid 7157 invoked by uid 0);
	Wed, 31 Dec 2008 17:22:12 -0000
From: Anacron <root@cube.cube>
To: root@cube.cube
Subject: Anacron job 'cron.daily' on cube
Date: Wed, 31 Dec 2008 19:22:12 +0200
Message-Id: <1230744132.954282.7156.nullmailer@cube>

/etc/cron.daily/apt:
Checking for new archive signing keys now
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```

The other 2 are the same as first.

---

### Post by blueridgedog on 2009-02-07
They seem benign and not a sight of a system compromise, so you are in good shape.  You can delete them or leave them as you see fit.  As you mentioned nullmailer is gone, so there error message is gone.  Good luck.

---

### Post by quincymd on 2009-02-07
These are output mails from cron/anacron.  Redirecting the output from your entries in crontab/anacrontab to /dev/null would stop the messages being queued for nullmailer.

I've also read that adding MAILTO="" to the begining of these tab files also stop these emails but would also stop other mailing output too.

---

### Post by PC_load_letter on 2009-08-02
Sorry to resurrect this old thread but I'm seeing similar messages in the syslog, they look like this: (Sa7 is my username)

```
Aug  2 22:00:06 Sa7 nullmailer[16649]: smtp: Failed: Connect failed
Aug  2 22:00:06 Sa7 nullmailer[5993]: Sending failed:  Host not found
Aug  2 22:00:06 Sa7 nullmailer[5993]: Starting delivery: protocol: smtp host: mail. file: 1240402939.6624
Aug  2 22:00:06 Sa7 nullmailer[16650]: smtp: Failed: Connect failed
Aug  2 22:00:06 Sa7 nullmailer[5993]: Sending failed:  Host not found
Aug  2 22:00:06 Sa7 nullmailer[5993]: Delivery complete, 110 message(s) remain.
```

When I went to the nullmailer queue folder there were a 110 messages, the first one is:

```
root@Sa7.Sa7
root@Sa7.Sa7

Received: (nullmailer pid 7655 invoked by uid 0);
	Sun, 22 Mar 2009 09:06:56 -0000
From: Anacron <root@Sa7.Sa7>
To: root@Sa7.Sa7
Subject: Anacron job 'cron.daily' on Sa7
Date: Sun, 22 Mar 2009 04:06:56 -0500
Message-Id: <1237712816.253281.7654.nullmailer@Sa7>

run-parts: /etc/cron.daily/apt exited with return code 1
```

And all of the rest look like this:

```
root@Sa7.Sa7
root@Sa7.Sa7

Received: (nullmailer pid 6705 invoked by uid 0);
	Sun, 02 Aug 2009 04:49:36 -0000
From: root@Sa7.Sa7 (Cron Daemon)
To: root@Sa7.Sa7
Subject: Cron <root@Sa7>  if [ ! -d /var/run/munin ]; then /bin/bash -c 'perms=(`/usr/sbin/dpkg-statoverride --list /var/run/munin`); mkdir /var/run/munin; chown ${perms[0]:-munin}:${perms[1]:-root} /var/run/munin; chmod ${perms[2]:-0755} /var/run/munin'; fi
Content-Type: text/plain; charset=UTF-8
X-Cron-Env: <MAILTO=root>
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Date: Sat, 01 Aug 2009 23:49:36 -0500
Message-Id: <1249188576.251653.6700.nullmailer@Sa7>

mkdir: cannot create directory `/var/run/munin': File exists
```

Now, should I worry about the security of the system, or are these messages just routine? How do I eliminate these messages to begin with? 

Thanks.

**EDIT: Both nullmailer & munin are installed on the system, which is Ubuntu 8.10 intrepid.**

---

