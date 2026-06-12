---
title: "EXT3-fs error"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by Aanaddor on 2009-10-12
Greetings,

I am new to this forum and Ubuntu.

I am getting an EXT3-fs error.

I have a Toshiba laptop with Windows Vista Home Edition and I installed Ubuntu 9.04 couple months ago and all worked fine until I decided to make the partition larger.

I went into windows vista and by using the partition manager that I have, I resized the partition and, when I rebooted the laptop I got an error 17, which I corrected by following the instructions in this [COLOR=DarkGreen]**[POST]("http://ubuntuforums.org/showthread.php?t=1086483")**[/COLOR] on the forum. [URL="http://ubuntuforums.org/showthread.php?t=1086483"]
[/URL]
I can now get into the Grub menu but I keep getting a new error. EXT3-fs error and the laptop hangs.

I can't even boot up using my Ubuntu's LiveCD nor my USB Ubuntu anymore, but I can get into Windows with no problems.

I hope this can be a simple error to correct, the last thing I want to do is loose my documents on that partition.

Any help would be most grateful.
Thanks.

Aanaddor

---

### Post by cariboo on 2009-10-12
You will have to go into the bios of your computer and set the correct boot order so that you can boot from the live cd. Once you have done that, boot from the Live CD and run fsck on your ext3 partition.

---

### Post by Aanaddor on 2009-10-13
> **cariboo907 said:**
> You will have to go into the bios of your computer and set the correct boot order so that you can boot from the live cd. Once you have done that, boot from the Live CD and run fsck on your ext3 partition.
I got the LiveCD to work. thanks. But how do I run fsck, and what commands I run with it?

I am a total noob to Ubuntu, sorry for my lack of knowledge.

---

### Post by oldfred on 2009-10-14
from the liveCD go to terminal and run 
fsck - <[COLOR=DarkRed]device[/COLOR]>

Terminal is in applications, accessories, terminal. you should get a command line.

I am not sure if in live CD whether you need sudo first or not:
sudo fsck -h 
or 
fsck -h

-h will give you list of parameters you can use

file system should not be mounted or you get an warning like 
WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

to get list of partitions

sudo fdisk -l 
   [COLOR=DarkRed]Device[/COLOR] Boot      Start         End      Blocks   Id  System
[COLOR=DarkRed]/dev/sdb1[/COLOR]   *           1       18700   150207718+  83  Linux


fsck -v  [COLOR=DarkRed]/dev/sdb1[/COLOR]

-v is the verbose option

---

