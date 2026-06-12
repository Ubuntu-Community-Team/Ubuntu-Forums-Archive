---
title: "Networking with Windows machines"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by gamelord12 on 2008-08-02
I can see my Windows machines on my laptop running Ubuntu, but I can't access any of the publicly shared files.  Also, my Windows machines don't see my laptop at all.  Before I re-installed my OS, this worked without me having to tweak anything.  What's wrong?

---

### Post by mb_webguy on 2008-08-03
Since you apparently have some experience with Samba shares, this might seem a bit basic and obvious, but...

Have you set any of your folders on Ubuntu up for sharing?  If not, you may not have installed the necessary Samba packages after your reintallation of Ubuntu.  Right-click on a folder in Nautilus, go to Sharing Options, check the "Share This Folder" box, and click "Create Share".  If you get a message asking if you want to install some packages, then that's your problem.

I've had things not work how I thought they should after an installation, only to realize I'd forgotten to do something simple like this... *shrug*

---

