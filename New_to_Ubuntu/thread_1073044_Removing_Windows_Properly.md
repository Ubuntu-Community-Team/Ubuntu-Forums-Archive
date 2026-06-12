---
title: "Removing Windows Properly"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by taminrob on 2009-02-17
Need some help...I have been running Ubuntu for about a year now and see no reason to continue keeping Windows XP on my laptop.  I originally installed Ubuntu 8.04 as a dual boot and partitioned my drive with the majority of space dedicated to Windows.  Now Windows will not even boot and it has been so long that I have even felt the desire to use it, that I just want to dump it and give over the whole drive for my use in Ubuntu.
So, my question is, how can I do this without having to completely start over now that I have Ubuntu set up just the way I want?
Thanks in advance for the help...

---

### Post by sandyd on 2009-02-17
type this in terminal

```

sudo apt-get install gparted

```

installs gparted partioining tool

```

sudo gparted

```

now heres the part where you have to be reeeeaaaaaally carefull


select your winxp partition, select delte, select apply.

Now, theirs two things you can do

1. Expand ubuntu partition.

right click on ubuntu partion, select resize

use max space :)
WARNING: BE CAREFULL ABOUT RESIZING. IF DONE IMPROPERLY, IT CAN DAMAGE YOUR UBUNTU INSTALLATION

OR
2. just right click and  reate a new partition on the free space you see right now. 
its safer, and gives you an extra partition to back up your files in case of faliure. (yes, i know. theirs millions of people saying ubuntu is bulletproof, but one of those days....)

---

### Post by taminrob on 2009-02-21
OK, I tried to follow your instructions and was successful in deleting the windows partition but gparted will not allow me to resize my ubuntu partition.  I have tried to unmount my ubuntu drives but it will not allow me to do that saying that it is mounted at / and is being used.  So I figured that I would just leave that as a separate partition and use that for file storage that way and formated it to ext3, so far so good, but it will not allow me to paste any information there and it has a folder placed there called lost+found that it says I dont have the necessary permission to view (I am the only user on this system and should have full access I would think) and wont give me the option to enter my password, so I have no idea what is in there.
So now I have 66 gig of free space, but cant figure out how to use/access it...HELP!

---

### Post by sandyd on 2009-02-21
chk in ur inbox....

---

### Post by RomeReactor on 2009-02-21
Hi. Whenever you want to resize partitions, make sure they're not in use. In this case, you tried resizing your Ubuntu partition to expand it. Try booting into a Live CD, if you have one, and use Gparted there.

---

### Post by presence1960 on 2009-02-21
pop in the live cd and use gparted from there. I may be wrong, but I think you can not resize a mounted partition. **If you go the resize route make sure you BACK UP your data please!!!!!**

---

### Post by taminrob on 2009-03-01
Let me just put a quick update here...I did a very bad thing, against advice, I attempted to do this without backing up my drive (didn't have an external drive to save to and was impatient about putting this off until I could get one, trying to save money is not always the right thing to do!) I want to say to anyone reading this...***__***DO NOT TRY TO REPARTITION A DRIVE WITHOUT SAVING YOUR DATA!!!  I found out the hard way that I have bad sectors on my drive and when trying to complete this operation they caused the repartitioning to fail.  I am now in the process of running photorec to recover files and pictures...it is working, but very slowly (over a week straight and still not quite half way there on a 120gb drive, those bad sectors I mentioned are really killing me), when that is complete I will attempt to reinstall a fresh copy of Ubuntu and see how things go from there.

ANYONE NOT SURE OF WHAT YOU ARE DOING, PLEASE LEARN FROM MY MISTAKE AND DO THIS THE RIGHT WAY...BACK UP AND SAVE!

---

