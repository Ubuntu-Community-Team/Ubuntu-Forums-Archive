---
title: "Denied permission to open autorun prompt on Western Digital External Hard Drive"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by lisabrown715 on 2009-06-30
I am brand new to Ubuntu so go easy on me.  I have an HP 530 laptop and I am running Hardy Heron.  I just connected a new Western Digital 500GB External Hard Drive.  It is recognized, but when I click open autorun prompt, I get a message that says Error starting autorun program.  Permission Denied.  Can you please help me?

---

### Post by halitech on 2009-06-30
chances are thats a windows autorun program and won't run in Ubuntu without WINE. However, you don't need to run the program to access the drive

---

### Post by lisabrown715 on 2009-06-30
WOW!  How did you answer so fast?  That was amazing.  Thanks.  So I just ignore that and can copy my photos to the hard drive with no problems?

---

### Post by halitech on 2009-06-30
ran into this a few times. You can ignore the message but chances are you can't copy anything to the drive yet. Can you open a terminal and post the results of
```
lsusb
``````
mount
``````
cat /etc/fstab
```

---

### Post by lisabrown715 on 2009-06-30
OK, here you go-[FONT=monospace]

infinitysquared@infinitysquared:~$ lsusb
Bus 002 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
infinitysquared@infinitysquared:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-rt/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
infinitysquared@infinitysquared:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=157c935d-ac29-4ce4-80a2-176b756e2b3f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c9f50d2b-a72f-47fe-b3a4-fa0621b9786e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
infinitysquared@infinitysquared:~$ 
infinitysquared@infinitysquared:~$ 

[/FONT]

---

### Post by halitech on 2009-06-30
looking over the info it looks like you should actually be good to go. Is this drive only going to be used on Linux or will it be connected to windows machines as well?

reason I ask is because of this
[color="red"]/dev/sdb1 on /media/My Book[/color]
the space could potentially cause issues

---

### Post by lisabrown715 on 2009-06-30
I currently have more photos on my laptop than I have space for.  I also have a ton of photos on my work computer which is Windows XP.  My intent is to move all those photos onto the external hard drive "one time", then I would probably not need to do it again.

---

### Post by halitech on 2009-06-30
ok, then I would suggest connecting it to a windows computer, renaming it without the space, disconnect properly and connect to the Ubuntu computer and make sure you can still read it. If you can, unmount it and copy your files over from the other computers. Once you have confirmed you can see the files in Ubuntu, then you can remove the files from the windows computers if you desire.

---

### Post by lisabrown715 on 2009-06-30
I will do what you suggest tomorrow at work and hopefully it will go well.  I'll be back if not.  One last question for tonight...how do I check my laptop easily to see how much free space I have?

---

### Post by halitech on 2009-07-01
good question, its been so long I'm not sure anymore. I think you can open My Computer and just click the C Drive and it will show on the left side the total size and the free space but I'm guessing on that cause its been awhile since I used windows.

---

### Post by niteshifter on 2009-07-01
Hi,

Er, I believe his laptop is running Hardy Heron. Three ways to see disk space.
Via the command line (in Terminal) type:
```
df -h
```
Graphical display:
Click Applications -> Accessories -> Disk Usage Analyser.
Click System -> Administration -> System Monitor. Click the File Systems tab.

---

### Post by halitech on 2009-07-01
doh, thats what I get for reading the forums before I've had enough caffeine injected into my system :(  was thinking of the work system for some reason.

---

