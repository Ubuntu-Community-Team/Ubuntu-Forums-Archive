---
title: "Installing Video Driver"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by Lee2010 on 2009-12-09
Ok so I am new to Ubuntu and Gnome and the whole terminal idea but I am learning... So here is my problem...

I am trying to install some Nvidia drivers in Ubuntu 9.10. Am I doing something wrong? This is my terminal

lee@Lee-Ubuntu:~$ cd /home/lee/Desktop
lee@Lee-Ubuntu:~/Desktop$ sudo sh NVIDIA.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 71.86.11...............................................................................................................................................................................................................................
  
Then  an error saying "You appear to be running an X server; please exit X before installing." appears... 
I tried pressing " ctrl alt F1" but the same error happened again. Any help would be nice

---

### Post by dwasifar on 2009-12-09
Installing nvidia drivers can be so twiddly that I usually take the cheater's way out and do it with Envy.  It's in the repos:

```
sudo apt-get install envyng-core envyng-gtk
```

Then just run **envyng** from commandline and it'll prompt you through the process, telling you what drivers are available and which are recommended for your card.

The downside is that you have to remember to undo what Envy does, if you're going to do a version upgrade or change the drivers some other way someday.

---

### Post by Malta paul on 2009-12-09
This link should cover what you need:
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)
:D

---

### Post by Lee2010 on 2009-12-09
The drivers for my card are not on the list it gives me.

---

### Post by 3rdalbum on 2009-12-09
You don't need to do any of that stuff.

Just go to System > Administration > Hardware Drivers and it will offer to install an Nvidia driver for you. The most appropriate one for your hardware.

If it doesn't offer this, then go into Synaptic Package Manager and hit the Reload button to load up the list of packages from the Ubuntu repositories.

---

### Post by Malta paul on 2009-12-09
I assume you have down loaded the drive for your card from NVIDIA,if so the method to install is the same as in the link.;)

---

### Post by Lee2010 on 2009-12-09
I followed the instructions on their site but how do I exit X to install the drivers?

---

### Post by 3rdalbum on 2009-12-09
> **Lee2010 said:**
> I followed the instructions on their site but how do I exit X to install the drivers?

Log out, press Control-Alt-F1, type:

```
sudo killall gdm
```

or

```
sudo service gdm stop
```

But I'm telling you, **use the version in the Hardware Drivers program if you possibly can. **It's better supported and will stay in sync with your kernel. If you install the driver from nvidia.com, you'll need to reinstall it every single time you upgrade your kernel.

---

