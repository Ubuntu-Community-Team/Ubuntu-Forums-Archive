---
title: "Ubuntu installations on Vista"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by uv2008 on 2008-12-24
Hello,

I have Windows Vista installed on my laptop computer, hard drive size 250GB. I would like to have Ubuntu installed on 50GB, and that the rest 200GB will remain Vista, and also to keep Vista as the default operating system when the computer starts up.
From reading the Ubuntu installation instructions it seemed to me that the Ubuntu installer can do the partitioning (rather than first doing the partition on Vista), so my question is what's the best way to do that and to keep Vista as default. 
Also, I've read that there is an option of "install inside Windows" - is it very different from the conventional installation, or perhaps I just got it all wrong?

Many thanks for your time and help.

---

### Post by halitech on 2008-12-24
with running vista I would probably use the vista tools to resize the drive and create a blank partition for ubuntu. 50gig should be more then enough room as you can mount storage space in the windows side to store things.
far as booting vista as your default, thats just a matter of editing grub once ubuntu is installed to make vista the default

installing inside windows could be 1 or 2 ways. you can use wubi to create a kind of virtual partition in the windows drive space and install ( you would still have grub to decide which OS to boot) or you can use a virtual machine to run ubuntu as a program inside windows.

---

