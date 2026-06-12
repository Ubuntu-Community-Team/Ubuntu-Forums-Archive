---
title: "How do I run my NVIDIA Driver?"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by flee0308 on 2011-01-24
Hi,

I am using a NVIDIA GeForce 8500 GT. I downloaded the driver for it for linux on NVIDIA website. I want to run it, but when I try to do "run in terminal", I get this error:

ERROR: nvidia-installer must be run as root 

I understand that this root is some sort of administrator, but how do I run my installer as root?

---

### Post by overdrank on 2011-01-24
Hi and maybe [RootSudo]("https://help.ubuntu.com/community/RootSudo") can help. :)
```
sudo sh NVIDIA-Linux-x86_64-260.19.29.run 
``` for example

---

### Post by 3rdalbum on 2011-01-24
Don't do it that way. Ubuntu already provides an official NVIDIA driver - just go to System,Administration, Additional Drivers to download and activate it in one step. Much easier than turning off X and running the installer as root, etc.

---

### Post by bonixavier on 2011-01-24
You could use the Nvidia drivers from the repository. AFAIK, they're the same binaries repackaged to Ubuntu. If you do want to install the Nvidia driver from its website, here's what you should do:

1- Do not install any proprietary drivers from the repository - they  will conflict with the driver you downloaded from Nvidia's website. If you already did, disable them.

That will make nouveau take over your video. Simply blacklisting nouveau doesn't work anymore. It's a problem that comes straight from Debian.

2- Disable nouveau permanently. In a terminal, type:```
echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf 
sudo update-initramfs -u
```3- Reboot and start in recovery mode.
4- Type telinit 3 then type your username and pw
5- Run the script you downloaded ```
sudo sh NVIDIA.....
``` and follow the instructions.
6- Reboot. Your Nvidia driver will work the next time you start your desktop.

---

### Post by linuxstew001 on 2011-01-25
> **3rdalbum said:**
> Don't do it that way. Ubuntu already provides an official NVIDIA driver - just go to System,Administration, Additional Drivers to download and activate it in one step. Much easier than turning off X and running the installer as root, etc.

Hi all. I am new to Ubuntu.  My question on this is...  I have the book and disk for v9.4 from Barnes and Noble.  When I try to run the disk live, it freezes up.  I have to run it on safe mode so the video won't crash. So then now I want to install the os.  Do I have to install it in safe mode? and then if I do, what is the process of loading Nvidia drivers?  I have a GT 7800 card...

---

### Post by Perfect Storm on 2011-01-25
> **linuxstew001 said:**
> Hi all. I am new to Ubuntu.  My question on this is...  I have the book and disk for v9.4 from Barnes and Noble.  When I try to run the disk live, it freezes up.  I have to run it on safe mode so the video won't crash. So then now I want to install the os.  Do I have to install it in safe mode? and then if I do, what is the process of loading Nvidia drivers?  I have a GT 7800 card...

The alternative is using the non-live CD that comes with text-installer interface. If you have problem with the live-CD. 

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by Ziskille on 2011-01-25
Ok after 20min of typing a guide that you can use or that might help I came across another thread that prohibits Users from explaining to other users how to log-in as root. Makes senses actually since it is a potentially catastrophic procedure of you screw something up lol. So with that said you can check out these links, they might help, sorry that I cant send you the guide, Ubuntu has spoken lol. 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://ubuntuforums.org/showthread.php?t=1674953&highlight=root+password](http://ubuntuforums.org/showthread.php?t=1674953&highlight=root+password)

---

