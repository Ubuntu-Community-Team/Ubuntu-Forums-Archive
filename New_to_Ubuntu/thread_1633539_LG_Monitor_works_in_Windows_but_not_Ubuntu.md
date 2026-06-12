---
title: "LG Monitor works in Windows but not Ubuntu?"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by entakt3 on 2010-11-29
Hi all

My problem is that my new LG Monitor does not work in Ubuntu 10.10
The monitor ran just fine in windows(vista) and i decided to try out Ubuntu and it work fine as long as i uses my old acer(small) monitor. But if i use my new LG(Wide) monitor then all i get is a black screen saying: Power saving mode..
Old monitor works. New monitor does not and i'am lost..

I would e grateful for any help =)
Sorry for my bad english..

Entakt3

---

### Post by khelben1979 on 2010-11-29
What is the exact model of this LG monitor and how is it connected?

---

### Post by germanix on 2010-11-29
It would help if you could post your LG model and serial number and also say which graphic card you use.

---

### Post by entakt3 on 2010-11-29
Hmm i can't figure out how to see the exact model of my monitor.. But here is what i can see.. 
How it is connected?  With a wire? (sry :oops:)

LG FLATRON Wide

Model No.    : L196WTQ - SF


Graphic Card : GeForce 9600 GT
Card Type    : PCI-E 8x
Video Ram    : 512 MB
GPU Frequency: 650 MHz

CPU(if needed).:Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz

---

### Post by CharlesA on 2010-11-29
We don't need the serial number, only the model number. I edited out serial number from the post.

---

### Post by endotherm on 2010-11-29
is there anything in your /etc/X11/xorg.conf ?
if so, you may have to regenerate it, using
```
sudo nvidia-xconfig
```
then reboot, and reenable your restricted driver, and reconfigure your nvidia-settings.

---

### Post by DogMatix on 2010-11-29
I have that very monitor on an Acer T180 desktop running Ubuntu 10.10. However, I only use the integrated nvidia graphics. I would imagine you have a driver issue.

---

### Post by khelben1979 on 2010-11-30
I just checked up [your monitor]("http://www.ciao.co.uk/Productinformation/LG_L196WTQ_SF__6759292") and from what I can see, it has an VGA input which would require a [VGA connector]("http://en.wikipedia.org/wiki/RGB_connector") or you can plug in a cable on the [DVI]("http://en.wikipedia.org/wiki/DVI_connector").

So there is no need to be embarrased, just check out the links above and report back on how it is connected.

Also, since this is a flat monitor, it has only one true resolution and if the Ubuntu graphic configuration file ( /etc/X11/xorg.conf ) have settings which conflicts with your monitor, then that might be the reason to why the monitor gets into powersave mode.

There might be that Linux have been unable to detect your monitor and in that case, it is possible to look into the configuration file. > less /etc/X11/xorg.conf or > less /usr/share/X11/xorg.conf.d and look into the #monitor section. It is not recommended to edit the configuration file unless you know what you're doing, using a tool to recreate the configuration file is to recommend and it has been suggested in this thread as well.

---

