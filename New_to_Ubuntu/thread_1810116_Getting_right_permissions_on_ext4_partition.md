---
title: "Getting right permissions on ext4 partition"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by cantbelikewater on 2011-07-22
Hello,

I currently have a separate partition which I share between 2 different versions of ubuntu (I have this setup because I need 2 different versions of gcc and other programs and ubuntu 11.04 could not downgrade, so installed 10.04). 

I was trying to run a program, which I created, but it gave me the error:

likewater@matrix:~/data/perl_code/michael$ ./tester.pl
bash: ./tester.pl: Permission denied

This program reads from a file then writes information into another file.

I followed this guide:[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

So I have already done the:
partition is mounted to /home/likewater/data
```
chown -R likewater:likewater  /home/likewater/data
```in addition to that I have also tried
```
sudo chmod go+w /home/likewater/data
sudo chmod -R +w /home/likewater/data
```Does it have anything to do with the permission options in fstab??
Right now my fstab has the line
```

UUID=1563fd12-6e58-4787-a9f9-73890917471b   /home/likewater/data  ext4   user,defaults  0  0

```

---

### Post by oldfred on 2011-07-22
Welcome to the forums.

I am no expert on ownership & permissions. Are you signing onto both systems with the same userID? I would think UID & GID should be 1000 regardless if both are Ubuntu or Debian based. Other systems may use different UIDs.

This is my fstab entry:

```
# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05 /mnt/data ext3 auto,users,rw,relatime 0 2

```

Since Hardy (or Intrepid), Ubuntu adds the relatime option by default.
relatime = relatime + defaults = relatime, rw, suid, dev, exec, auto, nouser and async

So my entry has some redundant settings.

What does this show you for ownership & permissions?

ls -l

---

### Post by cantbelikewater on 2011-07-22
UID is 1000 on both
and I did not make any groups, so they should both be in the default group
also the permissions came out like this on both:

```
drwxrwxrwx 8 likewater likewater 4096 2011-07-22 07:38 data

```

---

### Post by oldfred on 2011-07-22
then it just may be the file tester.pl is not set to executable?

Any script I want to run, I have to separately change permission to executable from either command line or Naulitus.

---

### Post by cantbelikewater on 2011-07-24
how do you make scripts executable?

i tried 
```
chmod +x filename
```
but it still gave me the same error

---

### Post by oldfred on 2011-07-24
I have used 

chmod a+x filename

But I am not sure what that difference is. I have also just used Nautilus and set execution.

If you do a ls -l of the file name?

I looked at a folder where I keep copies of script and my permisions are all over the place. Some I have not run (just one's I had saved) and they are not executable I now see.

```
fred@fred-MavericDT:~/Documents/LinuxDocs/CurrentSys/scripts$ ls -l
total 668
-rwxr-xr-x 1 fred fred   2100 2011-04-04 14:02 40_custom2011Apr
-rwxr-xr-x 1 fred fred   2144 2011-06-17 18:30 40_customJun2011
-rwxrw-rw- 1 fred fred   1786 2011-04-03 16:44 40_customNov2010
-rwxrwxrwx 1 fred fred    496 2011-07-21 15:28 AddFirstLineTxt.sh

```

---

### Post by cantbelikewater on 2011-07-24
```
rwxrwxrwx 1 likewater likewater   6279 2011-07-22 08:01 tester.pl

```I think I do have the permissions :(

One thing that is weird though is that in my partition, on ubuntu 10.04 it automatically creates a copy of what I put in the partition directory, and copies it to my home folder. I might have mounted it in some weird way. This does NOT happen in my ubuntu 11.04

*edit:*
In ubuntu 11.04 when I do "ls" tester.pl appears in green colored font, I think that signifies that the code is an executable, but again if I try to execute it with ```
./tester.pl
```
it gives me the same error message
```

likewater@matrix:~/data/perl_code/michael$ ./tester.pl
bash: ./tester.pl: Permission denied

```

Could it be that the partition is ext4??
Or did I mount it in a weird way?? What are proper mounting procedures?

---

### Post by oldfred on 2011-07-24
It is giving a bash error but is a .pl? Is that perl or php. I have only run bash & python.

for bash I normally run it 

sudo bash test.sh

---

### Post by cantbelikewater on 2011-07-24
Yeah, it's perl.
I tried
```
sudo bash tester.pl

```
but it didn't execute the code correctly

I also tried this:
```
likewater@Matrix:~/data$ sudo ./tester.pl
sudo: unable to execute ./tester.pl: Permission denied

```

---

### Post by oldfred on 2011-07-24
I know for both my scripts and python I have to have the correct first line to refer to the type of program to run. Is yours correct?

From a random perl file on my system and is perl in /usr/bin where it should be?
#!/usr/bin/perl

---

### Post by cantbelikewater on 2011-07-24
The code is correct, it runs perfectly fine on different partitions. (The default partition that contiains root and /home)
I just tried this guide:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

but i got the exact same errors :(

* Edit *

So i did 
```

likewater@Matrix:~$ ls -l /dev/disk/by-uuid

```

This is what came out
```

total 0
lrwxrwxrwx 1 root root 10 2011-07-24 17:12 0C78A80178A7E7A2 -> ../../sda1
lrwxrwxrwx 1 root root 10 2011-07-24 17:12 1563fd12-6e58-4787-a9f9-73890917471b -> ../../sdb8
lrwxrwxrwx 1 root root 10 2011-07-24 17:12 22E882EDE882BE93 -> ../../sda2
lrwxrwxrwx 1 root root 10 2011-07-24 17:12 31963c91-08a1-4b1f-9f39-9aeb4c491214 -> ../../sdb7
lrwxrwxrwx 1 root root 10 2011-07-24 17:12 41b950db-d8ea-43b4-b594-fb59859f5877 -> ../../sdb6
lrwxrwxrwx 1 root root 10 2011-07-24 17:16 5b1d1522-ef82-4df2-b298-8f6da0b5549a -> ../../sdb5
lrwxrwxrwx 1 root root 10 2011-07-24 17:16 94b4af5b-0a3e-46ba-97fd-eb71438a2070 -> ../../sdb9

```

the partition that I'm trying to get things to work on is the second one (sdb8) is there anyway to change the "root root" part?? or do I not touch that?

---

### Post by oldfred on 2011-07-24
It will not copy executeable bit normally so is it executable in this directory.

ls -s
likewater@matrix:~/data/perl_code/michael$ ./tester.pl

---

### Post by cantbelikewater on 2011-07-24
No it does not work in the /home/likewater/data directory
but it will work in /home/likewater

/home/likewater/data is where sdb8 is mounted to
ls -s gives me this
```

4 C++  4 geant  4 glut install  4 likewater  4 Papers  8 tester.pl

```

One thing to note. 
see this picture
[http://s111.photobucket.com/albums/n125/Crossfirex3/?action=view&current=Screenshot.png](http://s111.photobucket.com/albums/n125/Crossfirex3/?action=view&current=Screenshot.png)

on the left side of nautilus where it has the short cut to places like the likewater, Desktop, File System...
it has 190 GB Files listed as well as data, these are supposed to be the same partition, could this be the problem?? Also the screenshot was done using my 11.04 build, but 10.04 gets the same error.

---

### Post by cantbelikewater on 2011-07-25
I had to double post
tester.pl ran when i used 
```

sudo mount -t ext4 /dev/sdb7 /data

```BUT, this doesn't work when i restart the computer, I think it is because the fstab doesn't do this automatically "-t" must do something different from what I have been doing

how do i get it to do such a command when i start up the computer??

NOTE THAT:
I re-installed my 10.04 build and in doing so the drive that I was formerly sdb8 has changed to sdb7, the UUID is still the same though
also I change the folder to /data, which also doesn't matter

Here is the complete history
I boot up, it has been mounted by fstab automatically at start up
```

likewater@Matrix:~$ cd /data
likewater@Matrix:/data$ ./tester.pl
bash: ./tester.pl: Permission denied
likewater@Matrix:/data$ sudo umount /dev/sdb7
likewater@Matrix:/data$ cd ..
likewater@Matrix:/$ sudo umount /dev/sdb7
**likewater@Matrix:/$ sudo mount -t ext4 /dev/sdb7 /data**
likewater@Matrix:/$ cd /data
**likewater@Matrix:/data$ ./tester.pl**
From which file do you want to read data from?
Error: cannot open file  
likewater@Matrix:/data$ 

```./tester.pl is supposed to print out other things after I run it but I just broke it with ctrl+d as the code ran sucessfully. 

my new fstab is 
```
UUID=1563fd12-6e58-4787-a9f9-73890917471b /data               ext4    user,defaults               0        0

```

---

### Post by oldfred on 2011-07-25
I used to mount my data partition in root like you are doing. Someone suggested it might be better in /mnt but it should not make a difference.

I then link the folders in /mnt/data into my /home so I can easily see them.

More discussion in this thread:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)

---

### Post by cantbelikewater on 2011-07-25
what is the advantage to it being in mnt??
I decided to move the partition back to the home folder. Because I was getting some more permission issues doing anything in the /  folder, it is now in /home/likewater/storage
I had to rename the partition mount folder to storage because if it was named data it would automatically copy anything that changed in the home folder to the data partition.

But it still does not work upon boot. It mounts, but cannont execute files. Only when I do unmount then do the
```

mount -t ext4 /dev/sdb7 /home/likewater/storage

```
will it work, can you please tell me a way to do this type of mount command automatically??
And do you really think that doing things in the /mnt directory will change things?? I had to run some programs with complicated library paths so I don't really want to change the mount location if it won't make any differences.

---

### Post by oldfred on 2011-07-25
I do not think changing to /mnt would really change things. I think the suggestion to me was that it would be "more Linux" like. 

If it was appearing in two places you must have had a link. But part of the problem could be if mounting from two different distributions and something is different. I use many Ubuntus and mount my /data identically in all of them without any issue.

These are the setting I use.
        auto,users,rw,relatime

---

### Post by cantbelikewater on 2011-07-25
with the 
```
 mount -t ext4 /dev/sdb7 /home/likewater/storage

```
it only appears in one place

I'm using pretty much the same settings 
```

auto,user,defaults,rw,relatime 

```

---

