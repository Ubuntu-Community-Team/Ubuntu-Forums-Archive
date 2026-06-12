---
title: "Can't run installed Ubuntu 10.10"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by Dofe on 2010-12-17
Hello here's the deal

I am new to ubuntu, went from XP to ubuntu just yesterday. After several problems (with partitioning when sda1 was my primary ntfs so i had to format it into ext3 to bypass that 'no root file system is defined' ; then all lowercase lettering in user-name to enable forward etc. )
I have successfully installed and restarted my computer, 10.10 appears with 4..5 dots below as loading then screen flickers and comes back to some mode that i cant go forward. It has some lines with ok in the end it says checking battery but after minute or two the lines come:
init: rsyslog main process killed by ABRT signal
init: rsyslog main process ended, respawning

with numbers (1023,1086) etc ...i believe you know how it goes.
Sometimes i go from there to tty4 where it asks me username and password and when i type them i get this:
unable to cd to '/home/myusername' and it goes into circle.

I've tried partitioning in a different manner to have / , /home , /swap or / , /boot , /swap
i have 3 available partitions
1. 13GB
2. 4,4GB
3. 0.9GB

I would really appreciate the help because i don't want to go back to XP. I just want to install it and use it without any problems :/
Thank you in advance :)

Cheers, Semir

p.s. i include \var\log\dmesg.log

[http://www.stavi.net/download/2/dmesg.html]("http://www.stavi.net/download/2/dmesg.html")

---

### Post by amsterdamharu on 2010-12-17
When you boot and hold down shift it should show you a boot menu, choose recovery and then somting with dkpg reconfigure (not sure what exactly). Try this option and let it finish, when it's done just press control + alt + delete to restart.

---

### Post by napoleon3665 on 2010-12-17
i really dont even know how what u did is possible...just reinstall. seriously...its wayy too screwed to even try to fix at this point.

---

### Post by iosuna86 on 2010-12-17
It seems as if you were starting Ubuntu under recovery mode. 

So you just installed Ubuntu and all that started to happen? Did it happen right away?

I would just reinstall it. There shouldn't be problems after a fresh install.

---

### Post by Dofe on 2010-12-17
> **iosuna86 said:**
> It seems as if you were starting Ubuntu under recovery mode. 

So you just installed Ubuntu and all that started to happen? Did it happen right away?

I would just reinstall it. There shouldn't be problems after a fresh install.

well ok ..thats not a problem, just tell me how to partition the hdd i mean how much and what where:
how much for \ , \home , \boot , \swap  or other things that i dont know      ...or
can i just install on a 13GB partition ext3 to be \    and leave the rest to take care for itself.
i really dont know what to do

---

### Post by napoleon3665 on 2010-12-17
when you are on the screen that allows you to partition the drive, just check the mark that says "guided, use entire disk" then it will take care of itself.

---

### Post by Dofe on 2010-12-17
> **amsterdamharu said:**
> When you boot and hold down shift it should show you a boot menu, choose recovery and then somting with dkpg reconfigure (not sure what exactly). Try this option and let it finish, when it's done just press control + alt + delete to restart.

did dkpg on recovery and it just updated all packages leaving me again with the same two problems:
1.ABRT signal is killing something anything everything >< ;
2.when i type my user name and pass i get unable to cd \home ...
3.screen just goes black and i have to restart ...

---

### Post by Dofe on 2010-12-17
> **napoleon3665 said:**
> when you are on the screen that allows you to partition the drive, just check the mark that says "guided, use entire disk" then it will take care of itself.

can't do that ..i have 58GB of data on a separate partition that i need.

---

### Post by MrFaler on 2010-12-17
UNIX systems use the forward slash in path names, not the backward one ;-)

When you reinstall go with the advanced option when promted for a partitioning way.
I would go with a layout similar to the following:

```

Partition     File System     Mount Point     Size
/dev/sda1     ext2/ext3       /boot           100MiB
/dev/sda2     ext4            /               7500MiB
/dev/sda3     ext4            /home           Rest
/dev/sda4     swap            /swap           Double your RAM

```

---

### Post by Dofe on 2010-12-17
> **MrFaler said:**
> UNIX systems use the forward slash in path names, not the backward one ;-)

When you reinstall go with the advanced option when promted for a partitioning way.
I would go with a layout similar to the following:

```

Partition     File System     Mount Point     Size
/dev/sda1     ext2/ext3       /boot           100MiB
/dev/sda2     ext4            /               7500MiB
/dev/sda3     ext4            /home           Rest
/dev/sda4     swap            /swap           Double your RAM

```

Will try that, thank you
Just one more thing ..is it important that partitions go in that order or not, can i go like this:
/dev/sda1 ext4      /home  rest
/dev/sda2 ext4      /      7500MB
/dev/sda3 ext2/ext3 /boot  100MB
/dev/sda4 swap      /swap  dblRAM

---

### Post by iosuna86 on 2010-12-17
> **Dofe said:**
> well ok ..thats not a problem, just tell me how to partition the hdd i mean how much and what where:
how much for \ , \home , \boot , \swap  or other things that i dont know      ...or
can i just install on a 13GB partition ext3 to be \    and leave the rest to take care for itself.
i really dont know what to do

Since you have three partitions (13GB, 4.4GB and 0.9GB), I recommend you to leave the 13.8GB for /, 4.4GB for /swap and 0.1GB for /boot. That would be a good partitioning scheme for a system with 2GB of RAM.

Since you don't have that much space, you should at least have this in mind:

1. You swap partition should be 2x your memory size 
2. The boot partition should have something around 100-200MB (I have only used 53MB, so you may not need that much)
3. The rest can be given to /
4. Choose EXT4 instead of EXT3 when partitioning.

Hope that helped.

---

### Post by iosuna86 on 2010-12-17
> **Dofe said:**
> Will try that, thank you
Just one more thing ..is it important that partitions go in that order or not, can i go like this:
/dev/sda1 ext4      /home  rest
/dev/sda2 ext4      /      7500MB
/dev/sda3 ext2/ext3 /boot  100MB
/dev/sda4 swap      /swap  dblRAM

I don't think the order is important (I am not an expert), but you should keep in mind the following when installing Ubuntu:

1. check "primary" and "beginning" when giving size to the /boot partition
2. "beginning" to / and /home
3. "logical" and "beginning" to /swap

I followed the instructions of some user and it all went fine for me. It may not be necessary, but at least Ubuntu works like a charm with that configuration.

---

### Post by Dofe on 2010-12-17
It works!

Thank you again for your time.

I've just reinstalled it and partitioned it as you said and it works. From today i am new ubuntu user :D

Cheers !

---

### Post by iosuna86 on 2010-12-17
I am glad you can enjoy Ubuntu from now on!

---

