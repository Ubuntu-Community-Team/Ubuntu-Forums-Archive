---
title: "where all my drivers at"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by c.c.rascal on 2010-08-24
after booting ubuntu10.0.4 netbook rmx from my usb to my dell inspiron 1564 i cant seem to pick up my wifi or sound 
ive booted up 2 twice now from the usb then when booting back from my hard drive back to windows 7 i get a blue screen crash .After looking on this forum it seems this could b down to the drivers but i aint to sure as im a total noob to this

so if so howe do i get the drivers and where?
thanks any help or guidance will be very helpfull:p

---

### Post by dtoronto on 2010-08-24
Could be that there aren't any open source drivers for your hardware available yet, you may want to check the site of your hardware manufactures for any proprietary drivers or check to see if your Ubuntu distro can pick up the proprietary drivers from System > Administration > Hardware Drivers

---

### Post by c.c.rascal on 2010-08-24
propriety drivers ? im  not to sure what they are .so do you think i should have a look at dell and c what drivers are compatible for inspiron 1564 and my distro is 10.04?

---

### Post by oldsoundguy on 2010-08-24
First off booting from a USB drive into Ubuntu will do nothing to your existing hard drive on your computer unless you INSTALL it ON the drive, SOOOOOO, your Windows problem is a WINDOWS problem.
Could be something that was lurking in the background of Windows and COINCIDENTLY happened when you were running Ubuntu from that USB.

Stuff does NOT cross over from one system to the other as the file systems and operating systems are TOTALLY different.

---

### Post by c.c.rascal on 2010-08-25
> **oldsoundguy said:**
> First off booting from a USB drive into Ubuntu will do nothing to your existing hard drive on your computer unless you INSTALL it ON the drive, SOOOOOO, your Windows problem is a WINDOWS problem.
Could be something that was lurking in the background of Windows and COINCIDENTLY happened when you were running Ubuntu from that USB.

Stuff does NOT cross over from one system to the other as the file systems and operating systems are TOTALLY different.
soooo true that made sense that it wont or cant cross over and was a windows problem
so i just went and booted back from the usb again with no problems when booting back from my hard drive into windows no probs :D  
when in linux it is saying that i dint have the wireless drivers and that ubuntu cant get them due to my manufacturer(dell inspiron 1564) the drivers are broadcom com b43 wireless and also broadcom sta wireless aany suggestions thats for makeing sense to the senseless:)

---

### Post by arpanaut on 2010-08-25
What do you mean by usb...
Is this a usb attached hard drive, SSD drive or just a pen/flash drive?
How did you install to said drive?
Do you have the option to attach the 'puter to modum/router via ethernet cord so you can download the drivers via System>Administration>Hardware Drivers?

---

### Post by oldsoundguy on 2010-08-25
Running from the USB, you can NOT install drivers into the system .. and to top that Broadcom is a POS in most cases.  It takes an act of Congress (when the Republicans are not in attendance) to get Broadcom to work .. it will, just takes a lot of effort.

SO, running the USB of the build has told you that your computer will take a bit of work to get functional IF you should decide to install Ubuntu.

---

### Post by c.c.rascal on 2010-08-25
> **arpanaut said:**
> What do you mean by usb...
Is this a usb attached hard drive, SSD drive or just a pen/flash drive?
How did you install to said drive?
Do you have the option to attach the 'puter to modum/router via ethernet cord so you can download the drivers via System>Administration>Hardware Drivers?
i no i should of stated erlier that it was a usb pen drive is where i have ubuntu
yeah i could get ethernet cable , then where could i go for the said drivers ?
i am not wanting to  install it fully to hard drive as it is out of my depth:pso will try ubuntu from pen drive for now could they drivers i want for ubuntu  conflict with my windows drivers?
thanks for the help :)

---

### Post by arpanaut on 2010-08-25
If you have set up the pen drive with persistance, i.e. with a storage space included then you could install the drivers through the Hardware drivers utility in Ubuntu and the changes would "persist" through reboots. If not you would need to reinstall each time you reboot.

No... Like Las Vegas, What happens in Ubuntu stays in Ubuntu LOL

See:[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://www.pendrivelinux.com/what-is-persistent-linux/](http://www.pendrivelinux.com/what-is-persistent-linux/)

If you have a 1Gb. or larger drive you could set up persistance, the bigger the better.

Oh Yeah... Some Broadcom chipsets are easier than others... 
On my HP laptop the B43 and/or STA work great  YMMV

---

### Post by c.c.rascal on 2010-08-25
> **arpanaut said:**
> If you have set up the pen drive with persistance, i.e. with a storage space included then you could install the drivers through the Hardware drivers utility in Ubuntu and the changes would "persist" through reboots. If not you would need to reinstall each time you reboot.

No... Like Las Vegas, What happens in Ubuntu stays in Ubuntu LOL

See:[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://www.pendrivelinux.com/what-is-persistent-linux/](http://www.pendrivelinux.com/what-is-persistent-linux/)

If you have a 1Gb. or larger drive you could set up persistance, the bigger the better.

Oh Yeah... Some Broadcom chipsets are easier than others... 
On my HP laptop the B43 and/or STA work great  YMMVthanks i will set my pen to persistent i tryed it when setting the pen drive the first time but got an error mmm but me thinks me nos where  i went wrong :p so will let you know how i get on tomorrow thanks
take it easy

---

### Post by c.c.rascal on 2010-08-26
after starting my netbook this morning it only went and crashed again mm and its only happening when i put ubuntu in and booting from the usb pen drive 
im on a dell inspiron 1564, windows 7,3ram , and the only thing my laptop says it needs is wireless drivers 
but i  have not got a clue how this is happening as im booting from my usb pen drive?

---

