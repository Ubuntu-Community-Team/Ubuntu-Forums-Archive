---
title: "fixing ubuntu"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Konstabel on 2009-01-10
How can I fix ubuntu after I deleted some packages? I have a text login only. No internet connection to my linux machine. Have a bootable ubuntu usb. I do not want to lose what on my hdd is.

---

### Post by mikewhatever on 2009-01-10
You can try to install the deleted packages from the installation cd. The command to add cdrom is <sudo apt-cdrom add>.

---

### Post by JoshuaRL on 2009-01-10
Do you know what packages you deleted?  If so, it should be a simple apt-get away.

---

### Post by linuxisevolution on 2009-01-10
> **Konstabel said:**
> How can I fix ubuntu after I deleted some packages? I have a text login only. No internet connection to my linux machine. Have a bootable ubuntu usb. I do not want to lose what on my hdd is.


Login and type **sudo apt-get install ubuntu-desktop** and hit enter

This will install any packages you have missing. Then type ** sudo apt-get update** and then **sudo apt-get upgrade**


******If you have no internet and you have the Ubuntu cdrom, you can add the cdrom to /etc/apt/sources.list ( sudo nano /etc/apt/sources.list ) and you will find something about a cdrom, there will be a '#' symbol to the left of it, delete that symbol, and hit ctrl+X and hit 'y' and enter.

---

### Post by Konstabel on 2009-01-10
I don't have a cd rom only usb. What packages? That's something I don't know. Can I just install over the current installation?

---

### Post by linuxisevolution on 2009-01-10
> **Konstabel said:**
> I don't have a cd rom only usb. What packages? That's something I don't know. Can I just install over the current installation?


If you would like to reinstall, boot from from your flash drive and select install if it has that option. How did you install Ubuntu the first time? You can always download the cd.

EDIT: Get Ubuntu cdroms here:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by linuxisevolution on 2009-01-10
> **Konstabel said:**
> I don't have a cd rom only usb. What packages? That's something I don't know. Can I just install over the current installation?

Ubuntu-desktop package has all the dependencies ( packages from the originall install ) and if you missing anything from the default that is important, it's supposed to install them, but since you don't have internet connection...

---

### Post by Konstabel on 2009-01-10
It is an old server machine with no cd-rom. The first time I used a usb. I tried running install again, but it want's to format the hdd and I can't have that. I just need to install over the current installation.

---

### Post by Konstabel on 2009-01-10
> **linuxisevolution said:**
> Login and type **sudo apt-get install ubuntu-desktop** and hit enter

If you have no internet and you have the Ubuntu cdrom, you can add the cdrom to /etc/apt/sources.list ( sudo nano /etc/apt/sources.list ) and you will find something about a cdrom, there will be a '#' symbol to the left of it, delete that symbol, and hit ctrl+X and hit 'y' and enter.

There is nothing about a cd-rom or usb in this file.

---

### Post by linuxisevolution on 2009-01-10
> **Konstabel said:**
> It is an old server machine with no cd-rom. The first time I used a usb. I tried running install again, but it want's to format the hdd and I can't have that. I just need to install over the current installation.

I'm not sure at this point. You could just back up your data and then do the install. You could add the usb to /etc/apt/sources.list and then do the update just like with the cd, just change the directory that the cd would mount to to the directory that the usb flash drive mounts to, for instance,

/cdrom to
/media/disk

I have to leave soon, wish you luck.

---

### Post by linuxisevolution on 2009-01-10
> **Konstabel said:**
> There is nothing about a cd-rom or usb in this file.

The first line says "#deb cdrom:......"

Just remove the #.

---

