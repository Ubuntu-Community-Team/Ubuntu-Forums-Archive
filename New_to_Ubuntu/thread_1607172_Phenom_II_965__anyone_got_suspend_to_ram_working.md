---
title: "Phenom II 965 : anyone got suspend to ram working?"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by dixonstalbert on 2010-10-27
Hello

I am trying to find a DDR3 motherboard that will successfully suspend to ram. If you have done this, can you tell me what motherboard you are using?

thanks 

Dixon


I just built a desktop  PC using:

Phenom II 965 cpu

asus m4a88td-v evo usb3 motherboard

4 gig g-skill ripjaws 12800cl8d

rosewill 80+ powersupply

I tried every BIOS power setting and did repeated clean installs of ubuntu 10.04, 10.10, 10.10 64 bit and windows 7 64 professional on 2 different SATA drives but no luck.

I returned the motherboard to newegg.

I posted on vipasus.com/forum asking if anyone had ever successfully got suspend to ram to work on this board but no one answered. 
Hoping for better luck on ubuntuforums!

I still have the phenom II and it would be nice if I could find a compatible motherboard for it, but I read on internet that suspend to ram is broken on newer AMD cpu's. At this point I would not mind buying a whole new intel cpu and MB if it meant getting suspend to ram working.

---

### Post by cariboo on 2010-10-28
It really has nothing to do with the cpu, it depends on how the motherboard manufacturer has designed the bios. During Maverick testing, we were finding that system with the same hardware, but different manufacturers,  were having different results when  suspending or hibernating. 

In this case I'm talking about atom cpus and intel graphics chipsets, but there seemed to be quite a difference between the different brands even with the same hardware.

---

### Post by griamdu on 2010-11-05
Hi,

I bought an asus m4a89gtd pro usb3 mainboard with a phenom ii 955 a month ago. I have just find how to make suspend or hibernate working ! Just disable the USB 3.0 controller in bios settings...

I hope this is a temporary workaround... until got usb 3.0 devices !

---

### Post by martinwebster on 2011-03-11
> **griamdu said:**
> Hi,

I bought an asus m4a89gtd pro usb3 mainboard with a phenom ii 955 a month ago. I have just find how to make suspend or hibernate working ! Just disable the USB 3.0 controller in bios settings...

I hope this is a temporary workaround... until got usb 3.0 devices !

To confirm, this fix also works with an Asus M4A88TD-V EVO/USB3 with Phenom II 965 running Ubuntu 10.10/ Linux Mint 10 (tested on 32 bit only.)

---

### Post by gufide on 2011-03-23
I got an asus too and suspend/hibernate don't work at all. I made a little script here for an asus G60Jx (my computer)

 **[COLOR=Red]**Be careful!**[/COLOR]** It install a script to get keyboard light work too. If you didn't have it one, just delete the section keyboard light


**IF IT DIDN'T WORK**
go here:[http://ubuntuforums.org/showthread.php?p=9261807](http://ubuntuforums.org/showthread.php?p=9261807)


else


download here:
[ATTACH]186911[/ATTACH]

---

### Post by Greydog56 on 2011-04-07
Running 64bit Kernal 2.6.35-22 generic, wanted to confirm I'm able to suspend or hibernate after disabling  USB3 and SATA 6gb from the bios of my ASUS M4A88TD-V EVO. 

ASUS M4A88TD-V EVO
Phenom II X4 840 3.2GHz
16 gig G.SKILL Ripjaws DDR3 1333
GeForce 9500 GT 1GB

---

### Post by dixonstalbert on 2011-04-07
glad to hear new kernels work.

I returned the M/B and got a M4A88T-M. which also would not suspend.

I have got hibernate to work using tuxonice kernel (2.6.32-30-generic-tuxonice)- still no luck with suspend.

I am using ubuntu 10.04 64-bit as I use Festival 1.96 text2wave with the Nitech HTS voice library and this version is not supported by ubuntu 10.10.

---

