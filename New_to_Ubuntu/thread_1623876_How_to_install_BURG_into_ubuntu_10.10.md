---
title: "How to install BURG into ubuntu 10.10?"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by Rushyang on 2010-11-17
Hey guys,

I followed this [tutorial]("http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/").. At the beggining of the installation, This [screen]("http://img264.imageshack.us/img264/2328/screenshotr.jpg") appears. I don't want to mess up with my start up.. I wanted a suggestion how should I proceed through this.

Thank you.

---

### Post by zer010 on 2010-11-17
Fisrt, wow! BURG looks pretty cool, I might have to check it out....
Second, it looks like it's asking for confirmation to the changes made to grub.
While I can't say for sure, getting grub back up and running isn't very hard with your ubuntu install cd handy. 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by stoogiebuncho on 2010-11-17
BURG takes all of your GRUB settings and copies them to the BURG folders.  (Because BURG is just GRUB with some fancy layout stuff on top of it)

This screen is just checking to make sure you want to import your GRUB settings.  You do.  Just press OK.

I've been using BURG for a couple of months and I really like it.  As zer010 said, if it doesn't work for you, it's really easy to reinstall grub.

If you decide to use BURG, you'll need to make one more change to make sure that it updates itself when you download a kernel upgrade.  Open the /etc/kernel-img.conf file, find where it says update-grub, and change that to update-burg.  

If you run into other questions, don't hesitate to ask.

---

