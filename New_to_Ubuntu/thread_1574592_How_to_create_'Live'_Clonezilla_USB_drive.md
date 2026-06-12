---
title: "How to create 'Live' Clonezilla USB drive?"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by JEBB on 2010-09-14
I want to use Clonezilla for backups but I don't know how to make it a bootable flash drive.  I downloaded the zip file moved it to the flash drive and expanded it.  When I tried to restart my Dell Mini 9 from the USB, it wouldn't start from that drive.  Now what do I do?  Thanks.

---

### Post by sikander3786 on 2010-09-14
Haven't used Clonezilla for that purpose but you should surely check out remastersys. A great tutorial here.

[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

---

### Post by bodhi.zazen on 2010-09-14
> **JEBB said:**
> I want to use Clonezilla for backups but I don't know how to make it a bootable flash drive.  I downloaded the zip file moved it to the flash drive and expanded it.  When I tried to restart my Dell Mini 9 from the USB, it wouldn't start from that drive.  Now what do I do?  Thanks.

Try unetbootin

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Probably better then remastersys for what you are wanting to do.

---

### Post by C.S.Cameron on 2010-09-14
MultiBootUSB should work with Clonezilla:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by da burger on 2010-09-14
> **bodhi.zazen said:**
> Try unetbootin

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Probably better then remastersys for what you are wanting to do.

As a quick note, if your using unetbootin you'll want the .iso file not the .zip file I believe. I know the website says to use the .zip file for USB sticks but that's working in a slightly different way.

If you want to use the .zip file then I think you need to extract the archive, but the extracted files on the USB stick, and then set the bootable flag on the USB stick. To set that flag you will probably need a program like gparted.

Someone feel free to correct me if I'm wrong.
Angus.

---

### Post by bodhi.zazen on 2010-09-14
> **da burger said:**
> As a quick note, if your using unetbootin you'll want the .iso file not the .zip file I believe. 

That is a good point, I assumed the OP would read the instructions on the unetbooting site, which are for an .iso.

---

### Post by jtarin on 2010-09-14
> **JEBB said:**
> I want to use Clonezilla for backups but I don't know how to make it a bootable flash drive.  I downloaded the zip file moved it to the flash drive and expanded it.  When I tried to restart my Dell Mini 9 from the USB, it wouldn't start from that drive.  Now what do I do?  Thanks.
[There's a nice little tutorial here.]("http://www.pendrivelinux.com/install-clonezilla-on-usb/") If you still have problems post back.

---

