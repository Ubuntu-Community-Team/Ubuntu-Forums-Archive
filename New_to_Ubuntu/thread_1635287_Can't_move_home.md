---
title: "Can't move home"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by bj218 on 2010-12-01
I used to be able to move home but no more!! Something called "gvfs" seems
to be getting in my way. How do I move home now??

---

### Post by GrantStoner on 2010-12-01
Do you have a virtual file system anywhere? Or one that needs to be mounted? Try mounting the drive first if it's not. GVFS stands for GNOME Virtual File System.

---

### Post by bj218 on 2010-12-01
> **GrantStoner said:**
> Do you have a virtual file system anywhere? Or one that needs to be mounted? Try mounting the drive first if it's not. GVFS stands for GNOME Virtual File System.

I do not what a virtual file sys. is!! The attachment shows my C drive,
maybe that will help. I want to move home to /dev /sdc6 ie homeu.

---

### Post by NCLI on 2010-12-01
> **bj218 said:**
> I do not what a virtual file sys. is!! The attachment shows my C drive,
maybe that will help. I want to move home to /dev /sdc6 ie homeu.
May I ask why you need to move your /home?

Also, why not just copy it there, then edit /etc/fstab to mount /dev/sda6 as home?

Lastly, why do you have so many partitions O.o

---

### Post by GrantStoner on 2010-12-01
> **NCLI said:**
> Lastly, why do you have so many partitions O.o

I was wondering this same thing... SOOO many partitions, and a lot of unused space. Did you mean to do all that?

---

### Post by bj218 on 2010-12-02
> **NCLI said:**
> May I ask why you need to move your /home?

Also, why not just copy it there, then edit /etc/fstab to mount /dev/sdc6 as home?  NOTE I changed /sda6

Lastly, why do you have so many partitions O.o

Q1.About 2 weeks ago I lost my 250GB drive which I seem to do a couple of times a year (please don't ask why). I managed to recover a good deal of what was on it but not all. So now I want to BU some of my data on my 
100GB drive ie /dev/sda. /dev/sdb has windows on it.

Q2. That is exactly what I tried to do but "gvfs"would not let me. This is what I did "sudo cp -T /home/* /homeu" then I got the message that gvfs would not allow
this to happen.I have A LOT OF MY DATA on /DEV/SDC6 which I want to keep on any new operating sys. I install. Once I get home moved I will edit /etc/fstab to include 
/dev/sdc6.

Q3.I think I ans. this in Q1 ie 100GB drive!!

---

### Post by oldfred on 2010-12-02
This version excludes that file:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

The --exclude='/*/.gvfs' prevents rsync from complaining about not being  able to copy .gvfs, but I believe it is optional.  Even if rsync  complains, it will copy everything else anyway.  ([See here for discussion on this]("http://ubuntuforums.org/showthread.php?t=791693"))

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by bj218 on 2010-12-04
> **oldfred said:**
> This version excludes that file:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

The --exclude='/*/.gvfs' prevents rsync from complaining about not being  able to copy .gvfs, but I believe it is optional.  Even if rsync  complains, it will copy everything else anyway.  ([See here for discussion on this]("http://ubuntuforums.org/showthread.php?t=791693"))

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

I am not sure but I think I may have done what I wanted to do ie move 
home/bill to homeu/bill. The attached picture shows what I did in 
terminal yesterday but I got chicken at the end & moved home/bill back
to ubuntu.This morning I counted the items in home/bill=45 then I counted homeu/bill=62. Homeu is on a separate partation ie /dev/sdc6. Should I now remove home/bill from ubuntu if so how do I do it? I also added the following line to /etc/fstab.
"/dev/sdc6    /homeu      ext4      defaults,errors=remount-ro    0   1"

What is going on when it says "omitting directory" can I live "/home/back/bill" out?

---

### Post by oldfred on 2010-12-04
Not sure what you did with the cp -T command. It is my understanding you have to use cp -a to preserve ownership & permissions.

I tend to prefer rsync now but it should not make a difference if you are copying all the files.

When counting files are you also looking at all the hidden files & folders?

---

### Post by Penguin=) on 2010-12-04
Type this in the terminal:

```
rsync
```

---

### Post by bj218 on 2010-12-04
> **oldfred said:**
> Not sure what you did with the cp -T command. It is my understanding you have to use cp -a to preserve ownership & permissions.

I tend to prefer rsync now but it should not make a difference if you are copying all the files.

When counting files are you also looking at all the hidden files & folders?

-T is Source to Destination. Should I have also used -a?
Yes I was looking at all the hidden files & folders.

---

