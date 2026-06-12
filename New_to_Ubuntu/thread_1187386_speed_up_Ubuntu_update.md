---
title: "speed up Ubuntu update"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by saeeddeep on 2009-06-14
Hi,
I've a LAN of 10 PCs running Ubuntu 8.04
Q.1: Is there a way to speed up updates?
(i.e; update one machine from the internet then configure the rest PCs to update from this first machine.)
Q.2:  Also I want to know, where Ubuntu updates are downloaded? I want to save these updates on CDs for future use!

---

### Post by CatKiller on 2009-06-14
> **saeeddeep said:**
> 
Q.1: Is there a way to speed up updates?
(i.e; update one machine from the internet then configure the rest PCs to update from this first machine.)

I believe it's possible to create a local repository and add entries to sources.list for the other machines to have them look there for updates. I haven't ever done it, though, so I can't tell you how.

> Q.2:  Also I want to know, where Ubuntu updates are downloaded? I want to save these updates on CDs for future use!

/var/cache/apt/archives/

---

### Post by Elfy on 2009-06-14
Have a look at apt-cacher - it seems to be what you're looking for. There is a how to as well.

[http://ubuntuforums.org/showthread.php?t=564301](http://ubuntuforums.org/showthread.php?t=564301)
[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

---

### Post by Therion on 2009-06-14
> **saeeddeep said:**
> Q.1: Is there a way to speed up updates?
Go to System/Administration/Software Sources, "Ubuntu Software" tab  and click on the "Download from" button.  
Select "Other".
Click on "Select best server".
Let it run it's tests and use the server it determines is giving you the best result.

The results can be rather dramatic.

---

