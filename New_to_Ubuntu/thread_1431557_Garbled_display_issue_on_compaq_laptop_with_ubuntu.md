---
title: "Garbled display issue on compaq laptop with ubuntu 9.10"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by fjirousek on 2010-03-16
Hi All,
 
I'm relatively new to linux, but wanted to jump in by installing Ubuntu 9.10 on a PIII Compaq Presario 2700 laptop. I burned the iso and was able to install ubuntu, even though the graphics were very garbled. Even though Ubuntu is installed, it won't load and shuts down, I believe due to a resolution problem. Can anyone help me figure out how to edit the resolution and fix this problem. I've searched the forums but came up with little. Thanks in advance!
 
Fil

---

### Post by coffeecat on 2010-03-16
PIII laptop. How much RAM does it have? There may not be enough. The gnome desktop that comes with Ubuntu is a heavyweight. You may need to install a version of Linux with a desktop that uses less memory.

But before making a judgement, post more details of your hardware: how much RAM, graphics card, hard disc space.

I must log off now - late here -  but I'm sure someone else will come in with help if you post those details.

---

### Post by fjirousek on 2010-03-16
> **coffeecat said:**
> PIII laptop. How much RAM does it have? There may not be enough. The gnome desktop that comes with Ubuntu is a heavyweight. You may need to install a version of Linux with a desktop that uses less memory.
 
But before making a judgement, post more details of your hardware: how much RAM, graphics card, hard disc space.
 
I must log off now - late here - but I'm sure someone else will come in with help if you post those details.
 
Hi All,
 
  Here are the specs of my machine:
 
 
 
**Model **COMPAQ PRESARIO 2701US


 

**Processor **Intel® Pentium® III-M Processor 1.0GHz featuring Intel® SpeedStep™ Technology**System Bus **133 MHz system bus**Cache **512KB Integrated "On Chip" L2 Cache**Display **15.0" TFT SXGA+ Display**System Memory **512 MB PC133 SyncDRAM**Hard Drive **60gb UltraDMA Hard Drive**Optical Drive **Dual Optical Drives plus Floppy

• 8X DVD-ROM drive 

• 8X CD-RW drive (FutureBay™ II)

**Networking **10/100 BaseT Ethernet Port**Graphics **ATI Mobility Radeon M6 Graphics with 16MB dedicated video memory

• 4X AGP for enhanced video, graphics and 3D performance

• Maximum internal resolution of up to 1600 x 1200 x 16M; with external monitor - 1600 x 1200 non-interlaced

• 32 bit color provides up to 16M brilliant colors


• Compaq DVD Player/Navigator

---

### Post by paker on 2010-03-16
Did you know ATI graphics and ubuntu don't work well together?

---

### Post by fjirousek on 2010-03-17
> **paker said:**
> Did you know ATI graphics and ubuntu don't work well together?

Haha, I found that out today!

Fil

---

### Post by coffeecat on 2010-03-17
> **paker said:**
> Did you know ATI graphics and ubuntu don't work well together?

Well - maybe and maybe not. That's a gross over-generalisation. It depends on the particular graphics chipset. ATI support is getting better.

@fjirousek, it would be worth searching the forum for that particular ATI card and see what comes up. I'm posting from a laptop with the more recent ATI Radeon HD4200. It worked well enough in 9.10 with the open source driver (although I couldn't get 3d acceleration) but the proprietary driver was an unmitigated disaster.

I'm posting from the development version of the soon-to-be-released 10.04, and I'm getting compositing and 3d with the open-source driver. Which is a major step forward. Things might be different for your older graphics but it might be worth running the 10.04 live CD to see if it will be better. As you are new to Linux, you might find the pre-release of 10.04 challenging - it's still a bit buggy - but you won't have long to wait for the final (end of April). If you're interested, say so, and I'll post a link for the download.

For the rest - you have enough RAM and I can't see any other difficulty with your hardware specification.

---

### Post by paker on 2010-03-17
> **coffeecat said:**
> Well - maybe and maybe not. That's a gross over-generalisation. It depends on the particular graphics chipset. ATI support is getting better.

@fjirousek, it would be worth searching the forum for that particular ATI card and see what comes up. I'm posting from a laptop with the more recent ATI Radeon HD4200. It worked well enough in 9.10 with the open source driver (although I couldn't get 3d acceleration) but the proprietary driver was an unmitigated disaster.

I'm posting from the development version of the soon-to-be-released 10.04, and I'm getting compositing and 3d with the open-source driver. Which is a major step forward. Things might be different for your older graphics but it might be worth running the 10.04 live CD to see if it will be better. As you are new to Linux, you might find the pre-release of 10.04 challenging - it's still a bit buggy - but you won't have long to wait for the final (end of April). If you're interested, say so, and I'll post a link for the download.

For the rest - you have enough RAM and I can't see any other difficulty with your hardware specification.

Whatever I tried with my 4200 onboard graphics, I couldn't make it run stable. To make ati grphics work with ubuntu, one needs to have your experise. And I am glad to hear you are working on improved driver.

---

### Post by coffeecat on 2010-03-17
> **paker said:**
>  To make ati grphics work with ubuntu, one needs to have your experise. 

The only expertise I used in Karmic with the 4200 card was to install the proprietary driver in System > Administration > Hardware Drivers and then delete xorg.conf when I found it unsatisfactory. Deleting xorg.conf is the quick and simple way to take you back to the default open source driver for your card.

I'm sorry your experience was less happy.

---

### Post by fjirousek on 2010-03-18
> **coffeecat said:**
> Well - maybe and maybe not. That's a gross over-generalisation. It depends on the particular graphics chipset. ATI support is getting better.
 
@fjirousek, it would be worth searching the forum for that particular ATI card and see what comes up. I'm posting from a laptop with the more recent ATI Radeon HD4200. It worked well enough in 9.10 with the open source driver (although I couldn't get 3d acceleration) but the proprietary driver was an unmitigated disaster.
 
I'm posting from the development version of the soon-to-be-released 10.04, and I'm getting compositing and 3d with the open-source driver. Which is a major step forward. Things might be different for your older graphics but it might be worth running the 10.04 live CD to see if it will be better. As you are new to Linux, you might find the pre-release of 10.04 challenging - it's still a bit buggy - but you won't have long to wait for the final (end of April). If you're interested, say so, and I'll post a link for the download.
 
For the rest - you have enough RAM and I can't see any other difficulty with your hardware specification.
 
Hi Coffecat, thanks for the info. I will search around regarding the graphics card. If all else fails, I'll just wait until version 10.04 is worked out. Thanks for all your help!
 
Fil

---

### Post by bradmayne04 on 2010-03-18
> **fjirousek said:**
> Hi Coffecat, thanks for the info. I will search around regarding the graphics card. If all else fails, I'll just wait until version 10.04 is worked out. Thanks for all your help!
 
Fil
 
Whatever you do don't i repeat do not use wubi.  My other lappy had the same problem and I download wubi and it fixed the issue temporarily.  It messed up the MBR and alot of other stuff.

---

