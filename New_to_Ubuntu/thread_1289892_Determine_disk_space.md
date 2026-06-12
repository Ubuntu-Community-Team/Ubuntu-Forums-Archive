---
title: "Determine disk space"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by Amockineuropa on 2009-10-12
OK I loaded Ubuntu to run with Windows Vista it seems to do OK but I get crash reports when I tried to update Synaptic and can't seem to save/update anything do to lack of available storage space. I have a 140GB HD and I thought that it was divided equally between the 2 OS's. But it does not seem to be. I tried to redo my partitions and even reloaded BOTH of my OS and still I have this problem. I am new to this and I sure that I made a mistake - somewhere.
 
I am also getting error msg when trying to update:
 
"Failure to check for installed and available applications This is a major failure of your software mgt system. Please check for broken packages w/synaptic, check the file permisssions and correctness of the file '/etc/apt/sources.list' and reload the software info with 'sudo apt-get update and sudo apt-get install -f'.
 
HOW do I do all of this?

---

### Post by earthpigg on 2009-10-12
hi,

try typing this, please, and show us the output:

```
df -Th
```

---

### Post by Amockineuropa on 2009-10-12
It say that I installed on just 2.3g I used 2.1G used 94%
My laptop HD has 140GB how do I get it to install beside Windows

---

### Post by Amockineuropa on 2009-10-12
So Ubuntu installed on just 2.3 gb of disk space. How do I increase its available dissk space?
 I will try to re-partition my drive w/out destroying my OS

---

### Post by Amockineuropa on 2009-10-12
Help with repartition. I am  trying to repatition my HD it is asking for TYPE of partition (primary of Logical
Size, Location of the new partition, use as and mount point.

---

### Post by ConXtionS on 2009-10-12
Hi bro

you do seem to find the good problems dont ya????

lol

Ok... dont do anything RASH yet


I have seen them talk about some kind of disc partioner that wont ruin your system

so keep your chin up and keep updating your thread until some one smart can give ya a hand...

Good to see your name again

Jim

---

### Post by 3rdalbum on 2009-10-12
There are a couple of HOWTOs around which I currently can't find on Google :-)  But here's the basic description:

[http://georgia.ubuntuforums.org/showthread.php?t=1267238&page=3]("http://georgia.ubuntuforums.org/showthread.php?t=1267238&page=3")

FYI, When you click the "resize partition" option of the Ubuntu installer, there is a bar graph at the bottom of the window, and there is a little slider handle at the right of the bar graph. Click and hold down on this and drag it towards the left, and it allocates more space for Ubuntu. You're not the only one who has missed this; it's difficult to see the slider handle on a big hard disk.

---

### Post by Amockineuropa on 2009-10-12
Live and hopefully learn. I really need help with this one. I need to repartition. I have the following options: Type for the new partition -primary or logical
location for the new partition: beginning or end
Use as: ext3 journaling file system
             ext4 journaling file system
             ext2 file system
             FAT32 file system
             swap area
             reiserFS journaling file system
             JFS journaling system
Mount point:  /
                      /boot
                      /home
 Anybody understand this stuff?

---

### Post by ConXtionS on 2009-10-12
Hey that google thing seems PROMISING

See .. smart guys are EVERYWHERE

---

### Post by earthpigg on 2009-10-13
> **Amockineuropa said:**
> Live and hopefully learn. I really need help with this one. I need to repartition. I have the following options: Type for the new partition -primary or logical
location for the new partition: beginning or end
Use as: ext3 journaling file system
             ext4 journaling file system
             ext2 file system
             FAT32 file system
             swap area
             reiserFS journaling file system
             JFS journaling system
Mount point:  /
                      /boot
                      /home
 Anybody understand this stuff?

hi,

well, you can resize the partition from the ubuntu live cd without needing to reinstall. boot with the 'try without making changes' option, and then once it is booted go to system -> administration -> partition editor. shrink the windows partition, then grow the ubuntu partition, leaving everything else the same. 20gb should be sufficient for your ubuntu partition. hit apply, and go grab some coffee or watch a tv show.


before you do this:
-this is especially important. make sure you back up all important documents on your computer before you do this.
-dont do it during a storm or when power is more likely to fail. power failure during this = lost data, will likely need to reinstall EVERYTHING.
-this is especially important. read #9 here: [http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)
-in windows, run defrag first. some folks recommend running defrag multiple times. do so if you wish, it wont hurt anything and may help performance. please do it at least once, though.

please do all of that. failure to heed my friendly advice regarding any of the above is very likely to create very real problems for you.


and in the future on fresh ubuntu installs, the more or less standard answers are:
-always select 'manually partition'. 'mount point' is '/' (aka 'root'), 'use as' is 'primary', and 'ext4' is the 'standard' filesystem. though it is possible, i wouldnt recommend a typical home desktop install with less than 20gb. (as you saw, the 'guided install alongside existing operating system' partition option during install likes to be nimble and try to only use 2-3 gb partitions... which is stupid and silly. in my opinion.)

---

### Post by earthpigg on 2009-10-13
o, and you dont actually need to use a 'gparted live cd' for any of the above as mentioned in the FAQ i linked.... an ubuntu live CD is just as good.

system -> administration -> partition editor is gparted.

---

