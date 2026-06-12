---
title: "Nvidia Driver Manual Install"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by guitardennison on 2010-06-14
_**Specs:**_

hp dv7 quad 

Nvidia Geforce 320 1 gig 

dual boot windows 7 Ubuntu 10.04

---------------------------------------------------

    I logged on today to find an error message telling me that i was running in low graphics mode or something like that.  This came at no surprise to me because after upgrading my drivers through ubuntu i still experienced low graphics tearing and white boxes during a normal boot.  
   I have a decent amount of time to burn so i was wondering if anyone had experience of manually installing the Nvidia driver.  I have done some research and some people say you can break or crash your system if it is not completed correctly.  I just need ubuntu running smoothly.
-----------------------------------------------------------

Thanks
-Matt

---

### Post by philinux on 2010-06-14
Have you got nvidia-current installed?

---

### Post by guitardennison on 2010-06-14
> **philinux said:**
> Have you got nvidia-current installed?

yes but i believe it is the incorrect driver because when i did a check it said i had the advanced graphics geforce 400 installed not the geforce 320 in my comp.

---

### Post by guitardennison on 2010-06-15
any ideas?

---

### Post by wojox on 2010-06-15
You can use this how to, but you'll need to reinstall your driver after every kernel update. [Install nvidia Lynx]("http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx")

---

### Post by Bachstelze on 2010-06-15
The nvidia drivers in Lucid do support your 320. I also experience this behaviour (Ubuntu sometimes boots in "low graphic" mode) with my 9400, and generally a reboot will "fix" it (i.e. the computer boots normally the second time). I'm still not sure about what could cause this.

---

### Post by djzoid on 2010-06-15
I had a similiar problem but it was because I had not enabled the driver in admin>hardware drivers.

---

### Post by guitardennison on 2010-06-15
> **wojox said:**
> You can use this how to, but you'll need to reinstall your driver after every kernel update. [Install nvidia Lynx]("http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx")

I will give this a shot and update you later.  I hope to god that it works because i am sick of the horrible graphics during boot.

---

### Post by cryptotheslow on 2010-06-16
With the NVidia driver the boot splash screen will appear in low resolution unless you make some changes to the grub config to use the uvesafb driver during boot.

I followed the instructions here and it worked out really well, also sorts out the horrible resolution on the virtual tty (ctrl+alt+F1 etc) screens:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by wojox on 2010-06-16
> **guitardennison said:**
> I will give this a shot and update you later.  I hope to god that it works because i am sick of the horrible graphics during boot.

If your only problem is with the boot screen then use **cryptotheslow** instructions. I was under the impression this was happening all the time while logged in.

---

### Post by guitardennison on 2010-06-18
> **wojox said:**
> If your only problem is with the boot screen then use **cryptotheslow** instructions. I was under the impression this was happening all the time while logged in.
 
the low resoultion happens most often during boot.  I do catch some flichering while adjusting the volume(ya know the little black box in the top right).  Ive been busy with finals so i havnt even touched my comp.
 
low resoultion in general

---

