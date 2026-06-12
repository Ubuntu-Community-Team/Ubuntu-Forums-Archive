---
title: "ifstate problem"
date: 2005-09-20
forum: Networking &amp; Wireless
---

### Post by mjwood0 on 2005-09-20
I started up my laptop with my network card plugged in and got the strangest error.

```
Failure initializing /etc/network/ifstate
``` 

Doing some digging, I found that /etc/network/ifstate is a link to /etc/network/run/ifstate.  However, it seems that the file ../run/ifstate doesn't exist.

Couple questions...
1. How do I get this back?
2. How could this have vanished?

MJWood0

---

### Post by mlomker on 2005-09-20
That's a dynamic file...your real problem lies elsewhere.  Does your network card not work?  Have you looked through **dmesg | more** for other errors?

---

### Post by mjwood0 on 2005-09-20
Thanks for the quick reply.  I'm sure the card works since I'm in Windows right now using it <ugghhh>

I looked through my dmesg | more and can't see anything obvious.  I'll boot back into Ubuntu and look again though.

Also, this worked fine yesterday.  I'm just trying to figure out what changed and I can't think of anything.

Thanks,

MJWood0

---

### Post by mlomker on 2005-09-20
> I'm in Windows right now using it

I was asking if it wasn't working in linux.  Your post really only discusses the error message and not why it's a problem.

---

### Post by mjwood0 on 2005-09-20
Doh!  <head slap>

Little background:
  Dell Inspiron 8100 Laptop
  Linksys WPC54G v1.2 Cardbus Wireless Card via Ndiswrapper

All worked well until this morning (I did download the latest round of updates last night -- I think there were 3 of them).

The problem is that when Ubuntu boots, it tries to run ifupdown which fails due to the the error:
```
Failure initializing /etc/network/ifstate
``` 

Therefore, ndiswrapper fails and the card doens't do anything under Linux.  However, the power is on to the card and it appears to be detected when I look at my dmesg.  However, the above error never gets logged into dmesg.

Hope this is a little more info.  I really apreciate all the help.

MJWood0

---

### Post by mlomker on 2005-09-20
Ndiswrapper fails to load at all?  What does **ndiswrapper -l** give you?

Can you manually load it? **sudo modprobe ndiswrapper**

---

### Post by mjwood0 on 2005-09-20
I tried loading it manually via ndiswrapper and it tells me that there is a problem reading from ifstate.

Really confused by this one.

Thanks for the help!

MJWood0

---

### Post by mlomker on 2005-09-20
This is supposed to run at boot time, but give it a try:

```

sudo /etc/init.d/ifupdown stop
sudo /etc/init.d/ifupdown start

```

---

### Post by mjwood0 on 2005-09-21
Again, thanks for the help.

I tried those as well and they gave me some error regarding the fact that they couldn't see ifstate... very weird.

So I decided fight with this last night when I got home.  I booted into Ubuntu and the disk check that occurs every 30 restarts decided it needed to run.  Great!  Since I've been having problems, looked like a good idea.

Anyway, it found 1000's of errors and told me to run it fsck manually.  Did that and found 1000's more errors, mainly with the "magic number" of files and files of the "wrong type"

Anyway, after fixing all this, it told me I was done so I rebooted.  Now I get a kernel panic.  Strange since I don't believe the drive to have problems (but then again, one never knows).  Also, I'm very careful to always shutdown properly.

Looks like I'm going to have to re-install to repair all this.

Thanks for all the help!!!

MJWood0

---

### Post by mlomker on 2005-09-21
> Looks like I'm going to have to re-install to repair all this.


I'd advise doing custom partitioning and make sure that you use a filesystem with a journal (ext3 or reiser).  You'll also want to separate / from /home to limit your loses.  

[This thread](http://www.ubuntuforums.org/showthread.php?t=65649&highlight=manual+partition) has some information that might be useful.

---

### Post by mjwood0 on 2005-09-21
I had ext3 installed and my / (root) partition was seperate from my /home partition.

However, when I ran fsck, it said the journal was messed up and that the filesystem was not ext2.  I was really confused.

Anyway, I won't lose my files, but I will have to re-inistall.

Thanks so much for all your help.  It means a lot!

MJWood0

---

