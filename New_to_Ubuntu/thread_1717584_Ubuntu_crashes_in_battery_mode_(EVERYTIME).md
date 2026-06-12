---
title: "Ubuntu crashes in battery mode (EVERYTIME)"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by rez182 on 2011-03-30
Ubuntu 10.10 (First time linux user)
Asus k40ie
2.10GHz Core2Duo
2GB RAM
nVidia 512MB

My Ubuntu crashes in battery mode no matter what. works perfectly in A/C mode.
What to do? Please help...

---

### Post by Paqman on 2011-03-30
Do you have another battery you can try? Can you boot up into another OS or a LiveCD and see if the fault persists?

What i'm getting at is: can you isolate this to either hardware or software?

---

### Post by rez182 on 2011-03-30
> **Paqman said:**
> Do you have another battery you can try? Can you boot up into another OS or a LiveCD and see if the fault persists?

What i'm getting at is: can you isolate this to either hardware or software?
id say its software, since it works fine with win7, didnt try the LiveCD. any idea whats causing this?

---

### Post by Quackers on 2011-03-30
Does this happen only when you unplug the power cord from a running system?
If so the fix near the bottom of post #1 in this thread is for 10.04 and different makes of laptop, but it could be worth a try for you.

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by crispy_420 on 2011-03-31
It may not be a "crash" but rather OS and hardware not talking to each other correctly. I have Ubuntu on my netbook as a dual boot with Windows 7 Pro and had a similar issue. My system would always say the battery was dead or only a few minutes of charge left. Best part was my "dead" battery worked fine in Windows. So after a little digging I found others had a similar issue and it turned out to be an easy fix. I just booted into Windows, went to manufacturers website (in my case Acer) and downloaded the latest BIOS. After running **BIOS update** utility and booting into Ubuntu my problem was gone for good.

The current BIOS is Version 215 for you model, what version is yours?

---

### Post by rez182 on 2011-03-31
> **crispy_420 said:**
> It may not be a "crash" but rather OS and hardware not talking to each other correctly. I have Ubuntu on my netbook as a dual boot with Windows 7 Pro and had a similar issue. My system would always say the battery was dead or only a few minutes of charge left. Best part was my "dead" battery worked fine in Windows. So after a little digging I found others had a similar issue and it turned out to be an easy fix. I just booted into Windows, went to manufacturers website (in my case Acer) and downloaded the latest BIOS. After running **BIOS update** utility and booting into Ubuntu my problem was gone for good.

The current BIOS is Version 215 for you model, what version is yours?

my ubuntu is a dual boot with win7 ultimate too...im not sure how to check the BIOS version. can u give me some tips on this n how to update to the latest if its not already updated?

thanks...

EDIT: @quackers: yea it happens when i boot ubuntu from battery, also when i unplug the A/C power.

---

### Post by crispy_420 on 2011-03-31
Not sure I can get really specific as I don't share your exact model but start by heading over to Asus's support site at support.asus.com and grabbing the latest BIOS version. Also they say check out the manual but it is worthless and shows nothing. 

It is possible that like my motherboard your laptop BIOS may update through a utility actually within the BIOS. Dig around in there and see. If that is the option, extract that BIOS file downloaded earlier to the root of a drive and point to it with utility. Flashing should only take a minute or two and will require a restart. If you had some custom BIOS settings they may need to be redone.

But most importantly read the exact procedure from Asus yourself or check your manual. It may sound cliche but RTFM. You don't want this going south on you because a bad BIOS upgrade can and will kill the system. So be very careful.

---

### Post by rez182 on 2011-04-01
i just did a BIOS Update from 207 to 215. still Ubuntu does not run in battery mode. if this goes on ill have to quit Ubuntu :(

can anyone help me figure this out? really wanna stick to Ubuntu.
thanks alot.

---

### Post by rez182 on 2011-04-02
i noticed when the wifi is off, my ubuntu runs perfectly fine. so basically something does not go right when in batter mode and wifi switched on. any idea how to fix it now that its narrowed down?

---

