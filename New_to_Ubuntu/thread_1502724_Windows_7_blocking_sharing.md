---
title: "Windows 7 blocking sharing"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by slyrDVS on 2010-06-05
Very simple problem, I can see my Desktop (Running Windows 7) and I have configured it to be open but everytime I try to connect to it to get my patches it prompts me with a password and I try to use the windows login/pass combo and it repeats the process...

I installed samba and configured it to use the Network name for the windows computer, but it still prompts me. 

P.S.
I can see my linux share from Windows 7, but not vice versa... 

Any help?



PROBLEM SOLVED:

On the windows 7 computer create the Same credentials as you use to login on ubuntu and it'll pass you through (samba is installed and configured to use the network name)

---

### Post by MedianMajik on 2010-06-05
So, you can't see your windows 7 share from linux or you just can't see a samba share?  If you can't see the Windows 7 share you might need to install ntfs-3g or something similar as only Fat partitions are viewed without additional codecs by default in Ubuntu.

---

### Post by slyrDVS on 2010-06-05
No, I can see my samba share from windows 7. (Win7 viewing Ubuntu 10.04)

But when I attempt to connect to my windows 7 from Ubuntu 10.04, it prompts me with a login that has no valid credentials...

I have tried 3 combinations...
1. My Ubuntu Login
2. My Win7 login
3. Win7's Secret Super Admin account

and none of them get me into the computer...


Also the drive I am trying to access is NTFS... I just want to back up the files so I can get rid of MS for good... (As most of my games work on Ubuntu now >:D)

---

### Post by CharlesA on 2010-06-05
Check here: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
Also, maybe change the home group setting so that it uses username/passwords instead?

---

### Post by slyrDVS on 2010-06-05
> **CharlesA said:**
> Check here: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
Also, maybe change the home group setting so that it uses username/passwords instead?

 I'll try it right now, and as for what you mentioned I have attempted the sn/ps setting and it pulled the same thing on me...

Also I'm installing the ntfs-3g drivers right now... :D

---

### Post by MedianMajik on 2010-06-05
```
whereis smb.conf
```
Post the contents of your Samba config to help diagnose the problem.
```
sudo fdisk -l
```
Use this to make sure you Windows partition is showing up.
```
sudo mount -t ntfs -o nls=utf8,umask=0222 <pathto/windows/partition*> /media/c
```
Try this using the path from fdisk to mount your Windows partition (path will look something similar to /dev/hdb1).
```
sudo umount /media/c
```
This will unmount the Partition

I found [this useful post]("http://bobjunior.com/blog/ubuntu-samba-share/") on setting up Samba shares between Windows and Ubuntu.

---

### Post by slyrDVS on 2010-06-05
> **MedianMajik said:**
> ```
whereis smb.conf
```Post the contents of your Samba config to help diagnose the problem.
```
sudo fdisk -l
```Use this to make sure you Windows partition is showing up.
```
sudo mount -t ntfs -o nls=utf8,umask=0222 <pathto/windows/partition*> /media/c
```Try this using the path from fdisk to mount your Windows partition (path will look something similar to /dev/hdb1).
```
sudo umount /media/c
```This will unmount the Partition

I found [this useful post]("http://bobjunior.com/blog/ubuntu-samba-share/") on setting up Samba shares between Windows and Ubuntu.


Thanks mate for the ideas, but I solved it just a minute ago. 
I was on the right path, just needed one last thing. The same credentials on a "temp-account" on the win7 machine as my ubuntu machine.

---

### Post by MedianMajik on 2010-06-05
Great to hear you solved it.  Please add [Solved] to the title of this thread and best of luck

---

