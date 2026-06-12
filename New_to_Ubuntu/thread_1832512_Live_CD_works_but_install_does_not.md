---
title: "Live CD works but install does not"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by spdd3mn on 2011-08-24
I have been problems with installing Natty, Or any ubuntu Image for that reason. It is a new system build running the following

Asus P8P67 LE mobo
Intel Core I5 2500 Sandy Bridge
8 Gb Corsair Vengence 1600Mhz DDR3
using a Galaxy geforce 220gt
2 Sata II 500Gb Western Digital Carvair Black in Raid 0

I can run the Live CD or boot to live from USB Flash but I can't install at all. I have tried several CD's the DVD, and created USB installs which all work for the live but will not install.

I have tried the following versions

10.04
10.10
11.04
11.10

Install hangs at the Ubuntu splash screen and than it throws me to Busy Box and states it can not find the install media. But it just freaking booted from it to the live operating system....wha wha what???:confused:

Now I have read issues with the Marvel IDE driver but I need that for the CDROM I have which is only IDE not SATA so I can not disable it.

So than I tried the USB with the Marvel IDE driver disabled and it still would not install.

I am at a loss I have been using ubuntu for a couple years and never had so much trouble everything just works normally.

My dreams of the new system just for Ubuntu, instead of the old PC reused have become a nightmare.

I am almost ready to put windows 7 on this system and take my windows PC 

qx9650 
6gb ddr 2
geforce 250 gts sli 
xfx 780 mobo

and use that for ubuntu instead

Please help

---

### Post by fdrake on 2011-08-24
when you boot from usb, it should givr you the message check content of the booting media. what was the result?

---

### Post by spdd3mn on 2011-08-24
when I check the DVD or the USB it hangs at the splash screen with the white and red dots and than it says the same thing it can't find the live install media

I have verified all MD5 to be correct tried using the desktop and non raid, than using the alternate and raid makes no difference

---

### Post by fdrake on 2011-08-24
> **spdd3mn said:**
> when I check the DVD or the USB it hangs at the splash screen with the white and red dots and than it says the same thing it can't find the live install media
 can you post the link of the iso image that you used (link to the ubuntu.com website)?

---

### Post by spdd3mn on 2011-08-24
[http://debian.pop-sc.rnp.br/mirror/ubuntu/11.04/](http://debian.pop-sc.rnp.br/mirror/ubuntu/11.04/)


This is the latest one there has been several considering all I have tried.

---

### Post by fdrake on 2011-08-24
i don't know this url... [http://debian.pop-sc.rnp.br/??](http://debian.pop-sc.rnp.br/??)
maybe be ok but why don't try too use the official source, so we can understand what exactly is the problem?
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by spdd3mn on 2011-08-24
I got the link off this main page for the alternate download because of the raid.

---

### Post by spdd3mn on 2011-08-25
I have now downloaded another copy and made the USB flash install from the Ubuntu machine I can get the image to work and install on. I am not see any issues with the USB flash but on the system build I have....it all checks out and works.


Only difference is the raid configuration. So now later at home I will try without raid and only one of the 500 Gb hdd and see what happens.


I was trying the alternate install because of the raid and it was failing at the point of the software install and the automatic updates, I have tried manual updates, as well as no updates and it always fails at this point with the alternate install on the usb.

---

### Post by fdrake on 2011-08-25
what kind of raid r you trying to install? can you post the link of the HOW-TO that you are following?

---

