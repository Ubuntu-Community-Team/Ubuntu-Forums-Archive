---
title: "Youtube (flash) videos choppy in full screen"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by coasat on 2009-05-03
Hello. Whenever I play a youtube video in full screen the picture slows down and gets choppy. I've read a few posts that suggest problems with flash player. Is there an alternative?

I'm using the latest flash player in firefox. My OS is Xubuntu 9.04. If there is any other information you need, just ask..

I'll keep trying to solve the problem, and if I make any progress, I'll update the post. 

Thanks,

Coasat

---

### Post by coasat on 2009-05-04
I read this thread: [http://ubuntuforums.org/showthread.php?t=1138055&highlight=youtube+(flash) ]("http://ubuntuforums.org/showthread.php?t=1138055&highlight=youtube+%28flash%29")
and decided to uninstall flash and install ubuntu-restricted-extras and nothing has changed. 

I uninstalled flash by using:

sudo apt-get remove --purge flashplugin-nonfree

and by installing:

sudo apt-get install ubuntu-restricted-extras

Any one have any ideas?

Thanks,

coasat

---

### Post by aw4lly on 2009-05-04
Do you have the drivers for your graphics card installed? I'm assuming you have proprietary drivers for your graphics card that aren't installed. Go to 

System > Administration  > Hardware Drivers

---

### Post by blueridgedog on 2009-05-04
Try it after disabling desktop effects.  System -> Preferences -> Appearance -> Desktop Effects, then "none".

---

### Post by coasat on 2009-05-04
I'm using Xubuntu. I found Appearance under applications > settings > appearance. Although I can't find anything to disable desktop effects. 

I don't think there are any desktop effects running on my Xubuntu any way.  Do you know how else I can check this?

Thanks

coasat

---

### Post by Insanity01 on 2009-05-04
> **coasat said:**
> I'm using Xubuntu. I found Appearance under applications > settings > appearance. Although I can't find anything to disable desktop effects. 

I don't think there are any desktop effects running on my Xubuntu any way.  Do you know how else I can check this?

Thanks

coasat

Right click, change desktop -> visual effects
there should be 3, look for wich one is checked

---

### Post by mick222 on 2009-05-04
what graphics card do you have.A lot of older ati cards are not supported

---

### Post by coasat on 2009-05-05
I typed lspci:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
**00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)**
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
02:04.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
02:04.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

I think the one in bold is relevant to your question.

---

### Post by coasat on 2009-05-07
hi. I'm still stuck on this problem. any other ideas?

---

### Post by Eberhard on 2009-05-07
Hi

I have the same problem with laggy fullscreen in youtube using firefox. My graphic card is also an Intel 855GM. Hope you guys can help us.

---

### Post by coasat on 2009-05-07
Does any one think I should try a different browser. One that is less resource hungary? Or try another application that uses flash?

---

### Post by Eberhard on 2009-05-07
Try this:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

This worked for me - fullscreen flash in youtube worked perfectly. Didn't try anything else, though. I changed back to my old settings cause the considerable performance increase led to my fans working overtime resulting in noise:) But it was a very efficient update and it is definitely worth a try. Hope that helped.

---

### Post by coasat on 2009-05-07
Thanks Eberhard. I've read the thread and I'll give it a try. Although, I must say that my fans are working most of the time anyway. Probably because my laptop is old and the bearings in the fans have worn out, which means the fans have to work harder. 

How long did it take you to follow the procedure in the thread? If it takes long, I'll leave it for the weekend to try.

I'll tell you guys if I've got it working

thanks, coasat.

---

### Post by Eberhard on 2009-05-07
It took me less than 30 minutes but i didn't have to do the MTRR fix. If you're not too familiar with ubuntu/xubuntu then maybe around an hour.

---

### Post by coasat on 2009-05-07
1 hour is not too bad 

Another idea: would it be better to downgrade to Xubuntu 8.0.4 Hardy Heron? Flash and other things might work better.

---

### Post by Eberhard on 2009-05-07
I have no experience with 8.04, sorry. Jumped on the wagon at 7.10 and now upgraded to 9.04:)

---

### Post by coasat on 2009-05-12
Eberhard, this seems to have done the trick. Only took me 15 minutes. 

I can watch flash in fullscreen, however there does seem to be a tiny flicker at times, although its not a big problem. 

Thanks for your help guys,

coasat

---

### Post by philinux on 2009-05-12
I'll give this a go on my GF's lappy.

---

