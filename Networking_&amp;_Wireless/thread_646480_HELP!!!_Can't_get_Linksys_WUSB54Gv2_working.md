---
title: "HELP!!! Can't get Linksys WUSB54Gv2 working"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by jcsaxx on 2007-12-21
Ok, I am on my 3rd Linux distrubution and STILL can't get the Linksys wireless adapter WUSB54Gv2 to work.  I have tried Ubuntu 7.10, and couldn't understand any of the instructions.  I have tried FreeSpire and my mouse wouldn't work.  So now I'm using Xubuntu and as you probably know, its like Ubuntu.  I'm not getting anywhere at ALL.

I've read a little about WINE and about NDISWRAPPER, but its all a foreign languange to me.  It seems that all the instructions that I find are too difficult for me to understand, AND I think that the people writing them THINK that I'm already online using a wired connection.  I am NOT online with the Linux pc, but I only want to use a Wireless internet connection.

Any solutions?  Should I just give up and go back to using Windows?  Is there another Linux that would be easier for me to understand and use my wireless adapter?  Any ideas? 

THANK YOU.

---

### Post by Jdm111 on 2007-12-21
Use synaptic and install ndisgtk. When thats done go to system>administration>Windows wireless drivers. then click install new driver. Navigate to the cd that came with the dongle and find the .inf driver file. I don't were that will be because is use a belkin dongle which is crap.

---

### Post by cost123 on 2007-12-21
My belkin dongle is crap also!

---

### Post by Jdm111 on 2007-12-21
> **cost123 said:**
> My belkin dongle is crap also!

What problem are you having?

---

### Post by lahook on 2007-12-21
> **jcsaxx said:**
> Ok, I am on my 3rd Linux distrubution and STILL can't get the Linksys wireless adapter WUSB54Gv2 to work.  I have tried Ubuntu 7.10, and couldn't understand any of the instructions.  I have tried FreeSpire and my mouse wouldn't work.  So now I'm using Xubuntu and as you probably know, its like Ubuntu.  I'm not getting anywhere at ALL.

I've read a little about WINE and about NDISWRAPPER, but its all a foreign languange to me.  It seems that all the instructions that I find are too difficult for me to understand, AND I think that the people writing them THINK that I'm already online using a wired connection.  I am NOT online with the Linux pc, but I only want to use a Wireless internet connection.

Any solutions?  Should I just give up and go back to using Windows?  Is there another Linux that would be easier for me to understand and use my wireless adapter?  Any ideas? 

THANK YOU.


I got my wusb54gv2 working by following the instructions here [http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54](http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54)
also i got the latest version of ndiswrapper from sourceforge.net. because my laptop was locking up when the wireless usb adapter was connected.

don't forget to add the 2 files from a windows box to your ndiswrapper driver folder.i hope this helps you out

my laptop is a old gateway solo 9300 PIII 700 Mghz running Ubuntu Gutsy (7.10)

---

### Post by lahook on 2007-12-21
use the windows driver for wusb54gv2 it's probably different than the wusb54gsv2.

---

### Post by jcsaxx on 2007-12-21
Here is an update on my progress:

Now the Linux pc is showing the usb adapter, but as WIRED and still no internet connection.  As far as the post about using a different driver, I am already using the driver for Linksys Adapter WUSB54Gv2.

Any other ideas?

---

### Post by jcsaxx on 2007-12-21
Its working now.  The only thing that I did was something like "make install ndiswrapper-1.50" and then it did something it hasn't done before, and then just for the heck of it I rebooted with the adapter hooked up, and BOOM it works.  BUT when I did the install command, I got a message saying that "permission is denied", so I wouldn't think the install would go through.

OH well, as long as I can get online with it.  That is what matters.  Thanks for your help.

---

### Post by lahook on 2007-12-21
glad to here you got it working. it took me a lot trial and error and searching to get the right combination. the last thing i did was upgrade or reinstall ndiswrapper, to keep my laptop from locking up

---

### Post by walkerk on 2007-12-21
in the future, to compile yo need to do the following (i'll use ndiswrapper as an example):
```
cd ~/ndiswrapper
```
```
make
```
```
sudo make install
```

the reason you got a permission denied is because you didn't use sudo for **make install**. make install requires additions to directories (root) outside of your home directory.

---

### Post by strykrforce on 2008-01-05
> **lahook said:**
> I got my wusb54gv2 working by following the instructions here [http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54](http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54)
also i got the latest version of ndiswrapper from sourceforge.net. because my laptop was locking up when the wireless usb adapter was connected.

don't forget to add the 2 files from a windows box to your ndiswrapper driver folder.i hope this helps you out

my laptop is a old gateway solo 9300 PIII 700 Mghz running Ubuntu Gutsy (7.10)

I did the same then but mine doesn't connect to my network for some reason.

---

