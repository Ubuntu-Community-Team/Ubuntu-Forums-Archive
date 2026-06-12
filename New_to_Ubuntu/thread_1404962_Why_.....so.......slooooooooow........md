---
title: "Why .....so.......slooooooooow......."
date: 2010-02-12
forum: New to Ubuntu
---

### Post by JimmyJazz82 on 2010-02-12
This is my first post on the Ubuntu forums, and I am very much a noobie when comes to linux.  Been a MSFT-man up till about 6 months ago.  What experience I do have is with the previous versions of Ubuntu, including the UNR.  

Here is my problem:  I recently did a fresh install of 9.10 on my Acer Aspire One and for whatever reason the boot time is taking almost 5 minutes.  Maybe this is an unreasonable gripe, but it was one of the reasons why I liked Ubuntu to begin with.  UNR and the other regular version would boot in under 30 secs!  

Anyone else having issues with this?  It has been slow since the install, so it is not associated to any additions of software.  I don't know what other info I should include.  

If anyone has any pointers of how I could speed this up, I am all ears!  Thanks!

---

### Post by Satoru-san on 2010-02-12
once you have it booted can you please do this, in a terminal it is in the apps menu
```
dmesg > ~/dmesg
gedit ~/dmesg

```then copy and paste that into here using [code] tags as it is VERY long.

EDIT: >_< WELCOME TO THE FORUMS :)

---

### Post by lavinog on 2010-02-12
There were a couple of bugs reported about this already.
I would first make sure you apply all of the updates first.

---

### Post by k3lt01 on 2010-02-12
> **JimmyJazz82 said:**
> This is my first post on the Ubuntu forums, and I am very much a noobie when comes to linux.  Been a MSFT-man up till about 6 months ago.  What experience I do have is with the previous versions of Ubuntu, including the UNR.  

Here is my problem:  I recently did a fresh install of 9.10 on my Acer Aspire One and for whatever reason the boot time is taking almost 5 minutes.  Maybe this is an unreasonable gripe, but it was one of the reasons why I liked Ubuntu to begin with.  UNR and the other regular version would boot in under 30 secs!  

Anyone else having issues with this?  It has been slow since the install, so it is not associated to any additions of software.  I don't know what other info I should include.  

If anyone has any pointers of how I could speed this up, I am all ears!  Thanks!

Yes I have had this problem, [here is my thread]("http://ubuntuforums.org/showthread.php?t=1376994").

Ureadahead is the culprit, when you have a new install or an update that installs a file with an init script or a new kernel Ureadahead takes its time read every little bit of each file during boot up. In theory it makes the next boot up so much quicker but I am yet to be convinced of that. On my laptop it got to the stage where I was waiting ages, eating lunch etc while it was trying to boot. I eventually removed Ureadahead (and sreadahead I think was the other one) and have never had a problem since.

---

### Post by 3rdalbum on 2010-02-12
Interesting, I've not had this problem on my Aspire One. Mine boots up unbelievably quickly, even though the SSD stores data even slower than a medieval caligrapher.

You may find benefit from installing Lucid Alpha 2 and running all the system updates; the bootup is quicker and the mobile broadband works properly now.

---

### Post by NightwishFan on 2010-02-12
I have heard if you are using an SSD you should use the NOOP I/O Scheduler to improve performance and drive life.
[http://en.wikipedia.org/wiki/Noop_scheduler](http://en.wikipedia.org/wiki/Noop_scheduler)

---

### Post by 3rdalbum on 2010-02-12
> **NightwishFan said:**
> I have heard if you are using an SSD you should use the NOOP I/O Scheduler to improve performance and drive life.
[http://en.wikipedia.org/wiki/Noop_scheduler](http://en.wikipedia.org/wiki/Noop_scheduler)

I'm pretty sure I used to use it, but it still doesn't help much when the SSD's write latency is up to 9 seconds.

---

