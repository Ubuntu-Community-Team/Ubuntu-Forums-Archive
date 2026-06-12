---
title: "VMWare"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by allenbradley on 2009-04-20
I have an XP CD with Office 2007 licensed for my company. After having enough troubles with Vista, and it crashing after an update, I decided to install Ubuntu Jaunty on the entire hard disk instead of dual-booting. However, I need softwares like Office 2007, Fluent, AutoCad that have an institute-wide license, so I need XP. Then I came across this article on ubuntuforums which showed screenshots of XP running on ubuntu using VMWare-server ( the free one ). I have a couple of questions :
(a) Is there a lag in the operation of XP on VMWare ( ie when you move a mouse, it takes a while to move the same on the screen )
(b) Can I install AutoCad, Fluent, etc ?
(c) What are the limitations of the free VMWare version? Should I purchase a copy?

Thanks again

---

### Post by nandemonai on 2009-04-20
I had nothing but trouble with VMware on Jaunty.

I'd highly recommend Virtual Box 2.1.4 instead.

Faster than VMware and it has a open source version (the one I'm using).

I honestly can't fault it. Only issue I've had was the 2.2 version was buggy hence I'm recommending the 2.1.4 version.

---

### Post by allenbradley on 2009-04-20
Thanks for the quick response! Again, does virtualbox support installing, say, office inside xp? (forgive me, I'm not too familiar with the concept of virtual machines) 

Also is there a lag in using virtualbox?

---

### Post by nandemonai on 2009-04-20
It acts just like a real machine so it will support most anything you like.

One thing to note is lack of 3D acceleration though. The newer version of vbox does support this apparently but since I had issues with it I can't comment on it.

As far as speed goes, I can't tell the difference between my native XP install and my virtual one under Ubuntu.

It's really quite impressive.

---

### Post by sazan on 2009-04-20
> **allenbradley said:**
> Thanks for the quick response! Again, does virtualbox support installing, say, office inside xp? (forgive me, I'm not too familiar with the concept of virtual machines) 

Also is there a lag in using virtualbox?

Yes it does..

---

### Post by allenbradley on 2009-04-20
Thank you sazan and nandemonai! Then Virtualbox it is.

---

### Post by dmizer on 2009-04-20
> **allenbradley said:**
> (a) Is there a lag in the operation of XP on VMWare ( ie when you move a mouse, it takes a while to move the same on the screen )
This will depend on several things, but mostly the amount of memory you have available. The more the better. As long as you have at least 256M of free RAM, you should be fine. You should also be able to move seamlessly between Ubuntu and XP. On my Quad core with 4Gig of ram, my Virtual XP boots into a ready desktop in about 5 seconds.

> **allenbradley said:**
> (b) Can I install AutoCad, Fluent, etc ?
While virtualization is able to do most things, autocad and fluent will probably not work. Graphics are difficult for Virtual machines. Programs that are audio intensive will also cause problems.

> **allenbradley said:**
> (c) What are the limitations of the free VMWare version? Should I purchase a copy?

I've been using VMware server for a little over 2 years now. I can't imagine not having it. I also see no reason to purchase a license unless you need enterprise level support.

---

### Post by dmizer on 2009-04-20
> **allenbradley said:**
> Thank you sazan and nandemonai! Then Virtualbox it is.

Just did some research on virtual box (I haven't ever used it), and found this: [http://ubuntuforums.org/showthread.php?t=808245](http://ubuntuforums.org/showthread.php?t=808245)

So, it looks like as long as you have enough RAM, you should be able to get autocad working. Here's a post that indicates that fluent should work as well: [http://balkrishnapatankar.wordpress.com/2009/04/15/virtual-box-22/](http://balkrishnapatankar.wordpress.com/2009/04/15/virtual-box-22/)

---

### Post by allenbradley on 2009-04-24
Thanks for the detailed response, dmizer! I run a core2duo with 4 gigs of ram ( on a 32-bit system though : so seeing something like 3.7 ). Allocating close to 2 gigs should be no problem. I guess I'll try virtualbox first as you seem to indicate that autocad may not work on VMWare, and I need autocad for some summer work. Once the server load is reduced, I'll install jaunty and virtualbox, and post my results on this thread.

---

