---
title: "Rsync issue"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Tsu on 2010-01-11
Hi everyone,

Background information &#8211;

I have setup two ubuntu servers and now testing and learning how to setup a file server. I intend to set it up in a way that 1 server will synce all the daa incrementally to another every 5 minutes. So that if the primary server was to fail the second server can be used. (I will try implement Heartbeat system or Linux HA after I have mastered the syncing part)

What have I done &#8211; 

I followed the guide to setup a basic default samba configuration.
I followed the guide linked below to setup Rsync.

[https://help.ubuntu.com/community/rsync#Using%20rsync%20with%20SSH%20for%20a%20Simple%20Backup](https://help.ubuntu.com/community/rsync#Using%20rsync%20with%20SSH%20for%20a%20Simple%20Backup)

I have two issues with Rsync &#8211;

1>	When I run the following command.

[COLOR="Red"]
sudo rsync -avv -e ssh /srv/samba/share/ test@192.168.5.2:/srv/samba/share/[/COLOR]

I am asked for a password for the remote server. (I intend to setup a crontab with the following command - */5 * * * * sudo rsync -avv -e ssh /srv/samba/share johnathan@192.168.5.7:/srv/samba/share to make this sync automatic)

2>	When I enter the password and I gain access to the remote server.  I get the following output.

[COLOR="Red"]building file list ...
20 files to consider
share/test.ppt
     1946624 100%   91.26MB/s    0:00:00 (xfer#1, to-check=59744/59746)
share/test.doc
      132608 100%    6.02MB/s    0:00:00 (xfer#2, to-check=59743/59746)
share/test.PDF
      531456 100%    7.24MB/s    0:00:00 (xfer#3, to-check=59742/59746)
share/test.DAT
          81 100%    1.03kB/s    0:00:00 (xfer#4, to-check=59741/59746)
share/test.xls
     9636864 100%    8.55MB/s    0:00:01 (xfer#5, to-check=59740/59746)
share/test.txt
         256 100%    3.79kB/s    0:00:00 (xfer#6, to-check=59739/59746)
rsync: recv_generator: mkdir "/srv/samba/share/test01" failed: Permission denied (13)
*** Skipping everything below this failed directory ***
rsync: mkstemp "/srv/samba/share/test02 " failed: Permission denied (13)
share/test03/
rsync: recv_generator: mkdir "/srv/samba/share/test03" failed: Permission denied (13)
rsync: mkstemp "/srv/samba/share/.Script.bat.6XFy42" failed: Permission denied (13)
rsync: mkstemp "/srv/samba/share/.Thumbs.db.lKuwG4" failed: Permission denied (13)
rsync: mkstemp "/srv/samba/share/.robocopy.exe.seOvi6" failed: Permission denied (13)
rsync: mkstemp "/srv/samba/share/.server.dbs.T8gwW7" failed: Permission denied (13)
rsync: mkstemp "/srv/samba/share/.server.ini.0ApzA9" failed: Permission denied (13
total: matches=0  hash_hits=0  false_alarms=0 data=12368331
rsync: failed to set times on "/srv/samba/share/.": Operation not permitted (1)
sent 14133075 bytes  received 346 bytes  2569712.91 bytes/sec
total size is 44931737174  speedup is 3179.11
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]
[/COLOR]

I do not know why rsync will not has permission issues. I can use the test account to access these files just fine remotely from my XP pro computer.

The file permissions to a file is show as an example below -

[COLOR="Red"]-rwxrw-r--  1 root test  132608 2009-05-27 11:01 test.doc[/COLOR]

The file permissions to a folder is show as an example below -

[COLOR="Red"]drwxr-xr-x  4 root test    4096 2009-09-18 15:59 01 test01[/COLOR]

Thanks for the help in advanced

---

### Post by J V on 2010-01-11
Try grsync, its a frontend for rsync... set it up there and mabey you'll notice a problem...

Edit: The files on the server are listed to root and the group test, test doesn't have write permissions....

```
sudo chown -R test /srv/samba/share
```

---

### Post by Tsu on 2010-01-11
Hi J V,
I changed the ownership as you instructed to test. The same error output appeared when I ran the command. Thanks for the help anyway.

---

### Post by J V on 2010-01-11
sudo chown -R test:test /srv/samba/share

---

### Post by Tsu on 2010-01-11
Hi J V,

Ran the command you stated, then the command to start rsync. Same output about permissions denied occurs.

---

### Post by J V on 2010-01-11
well is test really the name of the user you are using to rsync?

---

### Post by Tsu on 2010-01-11
The name of the user is not test. However I did make the necessary changes so that the command was relevant to the username.

This is the out put when I type ls -l:

drwxr-xr-x 15 test test    4096 2009-09-18 17:51 08 test01

---

### Post by barnex on 2010-01-11
If you want to run the job from cron, you'll want to set up an ssh keypair so that you don't have to enter a password.
There are many tutorials on this. Personally, I like to use the program "seahorse": just click 'Create ssh key', then 'Set up for ssh', and you're done.

---

### Post by J V on 2010-01-11
you still didnt set it right, find the user you are using and replace test with that user in the last line...

---

