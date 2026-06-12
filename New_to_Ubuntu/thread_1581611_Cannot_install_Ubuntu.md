---
title: "Cannot install Ubuntu"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by Tally on 2010-09-25
I have just begun the process of using Ubuntu. I have Vista SP 1. 
 
I found the download instructions very confusing!!! I downloaded 10.10 onto a memory stick. Then when when I clicked in the 'image' file", I was asked to insert a disk. Error message appeared. I then tried again and downdowed onto Disk. then saw intruction to download installer. I tried running but nothing happehed. Then saved to C:Program Files....................Now what?

---

### Post by wozzroo on 2010-09-25
Follow this tutorial. Maybe it will help.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)


 It's what I did, but I had problems at the end with booting. Don't know if I made a mistake somewhere along the line, so follow it closely, use the "show me " buttons a lot.

---

### Post by Tally on 2010-09-25
> **wozzroo said:**
> Follow this tutorial. Maybe it will help.
 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
 
 
It's what I did, but I had problems at the end with booting. Don't know if I made a mistake somewhere along the line, so follow it closely, use the "show me " buttons a lot.
 
This is this site that I used. It says...
**[COLOR=blue]If you're running Windows[/COLOR]**
 
[COLOR=blue]You can use Ubuntu Windows installer to run Ubuntu alongside your current system.[/COLOR]
 
I just don't get it. Are we suposed to create 2 disks?
I have now tried copying the 'ímage' to the hard drive but don't not know how to install. The installer that I down loaded has no effect.

---

### Post by philinux on 2010-09-25
> **Tally said:**
> This is this site that I used. It says...
**[COLOR=blue]If you're running Windows[/COLOR]**
 
[COLOR=blue]You can use Ubuntu Windows installer to run Ubuntu alongside your current system.[/COLOR]
 
I just don't get it. Are we suposed to create 2 disks?
I have now tried copying the 'ímage' to the hard drive but don't not know how to install. The installer that I down loaded has no effect.

I would not recommend Wubi. To try out ubuntu the livecd or live usb is a good way to play with the OS without actually installing.

Have a read through this. Make sure you've backed up anything important first and that you got your windows reinstall disks handy just in case you need them.
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by waynefoutz on 2010-09-25
> **Tally said:**
> This is this site that I used. It says...
**[COLOR=blue]If you're running Windows[/COLOR]**
 
[COLOR=blue]You can use Ubuntu Windows installer to run Ubuntu alongside your current system.[/COLOR]
 
I just don't get it. Are we suposed to create 2 disks?
I have now tried copying the 'ímage' to the hard drive but don't not know how to install. The installer that I down loaded has no effect.

You have to create one disk. The image file (.iso) is just a snapshot of the disk. Like a .zip file, it has all the stuff it needs compressed into it.  You need to write the image file to disk with one of the programs listed in the tutorial. Simply copying the .iso file to a cd isn't going to work.

Wubi is a way of installing without partitioning your drive. No permanent changes are made and it can be undone with Windows Add/Remove programs. You can use the wubi.exe to download the iso and install that way without burning a disk. But, you're better off burning the disk in the first place, then if you want to install Ubuntu "wubi-style" just insert the Ubuntu disk while windows is running and select "install as a Windows program."  

Basically there are two ways to install. Normal and Wubi.
Wubi is not a real install. It writes a big file in your Windows drive and fools Ubuntu into thinking it's a hard drive. This is great for beginners who want to try Ubuntu for a few weeks and don't want to make the commitment of splitting their hard drive into two or more partitions. Just understand that this method of installing is not very stable, and not meant to be permanent. You can use the wubi.exe file, it will download the cd image, for you, and install without the need for burning it. Or you can burn the disk from the main Ubuntu .iso, and insert the disk while Windows is running. 
To install normally, you have to boot with a normal Ubuntu disk that you have burned. This will boot up Ubuntu as a Live CD. You can try Ubuntu out that way, but you can't install anything or make any permanent changes because it's running off the cd. You can then click on the Install icon and install Ubuntu to your hard drive. You can either tell it to replace Windows or split your hard drive in two and dual boot both operating systems. 

I hope this clears it up. You almost need a flow chart with all the options....

---

### Post by waynefoutz on 2010-09-25
> **philinux said:**
> I would not recommend Wubi. To try out ubuntu the livecd or live usb is a good way to play with the OS without actually installing.

Have a read through this. Make sure you've backed up anything important first and that you got your windows reinstall disks handy just in case you need them.
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Also a lesson I learned the hard way. After Ubuntu partitions your drive, if Windows wants to do a scan disk the first time you run it after the partitioning, let it do so. Skipping it or stopping it midstream like I did will cook your Windows install.

---

