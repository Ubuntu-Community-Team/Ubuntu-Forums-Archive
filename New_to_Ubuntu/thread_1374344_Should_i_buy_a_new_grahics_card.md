---
title: "Should i buy a new grahics card?"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by nnjond on 2010-01-06
Hi,

I've been living in low scrn res hell since I installed 9.10. and although i've received lots of advice, nothing has got me back to my preferred spec of 1200 x 1600 @75/85 Hz.  If its just a matter of me buying a more up to date graphics card, I'm willing to do it. But how do I know if that is a solution?

---

### Post by arochester on 2010-01-06
What graphics card do you have now?

---

### Post by Zoot7 on 2010-01-06
> **arochester said:**
> What graphics card do you have now?
+1

And if you are looking at something new, I'd recommend you make damn full sure it's an nVidia card, you'll have a lot less problems that way.

---

### Post by ratcheer on 2010-01-06
I only paid about $40 for a new nVidia 9400GT card with a gig of memory a few months ago. So I say, go for it.

---

### Post by Bartender on 2010-01-06
> **ratcheer said:**
> I only paid about $40 for a new nVidia 9400GT card with a gig of memory a few months ago. So I say, go for it.

+1 

I've dropped two ASUS EN8400GS (fanless) cards into two different Linux boxes and they've worked fine after downloading the nVidia drivers.  I wish we had a better option than relying on nVidia but at this point in time it seems to be what we've got.

---

### Post by nnjond on 2010-01-07
I don't play games so don't need a great card. Do I need a more suitable one?

$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
nnjond@den-desktop:~$

---

### Post by nikhilbhardwaj on 2010-01-07
> **nnjond said:**
> 
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
nnjond@den-desktop:~$

you already have a graphics card
ans since you don't play games
its a waste of money

have you configured your card correctly
ie installing the correct drivers you need the 173.xx series and not the 190.xx series

---

### Post by nikhilbhardwaj on 2010-01-07
> **nnjond said:**
> 
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
nnjond@den-desktop:~$

you already have a graphics card
ans since you don't play games
its a waste of money

have you configured your card correctly
ie installing the correct drivers you need the 173.xx series and not the 190.xx series

---

### Post by sadaruwan12 on 2010-01-07
Could you please tell us the make and model of your graphic card

---

### Post by cascade9 on 2010-01-07
> **sadaruwan12 said:**
> Could you please tell us the make and model of your graphic card

Its in the lspci output- "GeForce FX 5500" 

I pretty much agree with nikhilbhardwaj, you've already got a video card, and it should go wayyyy past 16000x1200. You probably just have the wrong drivers, or no drivers at all. 

The only reason why you might want a new card is for VDPAU- nvidia video hardware decoding under linux/unix. Unless you watch lots of video files, or are having issues with video files currently, its just not worth it to buy a new card.

---

### Post by speedwell68 on 2010-01-07
> **nnjond said:**
> Hi,

I've been living in low scrn res hell since I installed 9.10. and although i've received lots of advice, nothing has got me back to my preferred spec of 1200 x 1600 @75/85 Hz.  If its just a matter of me buying a more up to date graphics card, I'm willing to do it. But how do I know if that is a solution?

> **nnjond said:**
> I don't play games so don't need a great card. Do I need a more suitable one?

$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
nnjond@den-desktop:~$

Go to the 'System' menu and choose 'Adminstration' and the 'Hardware Drivers'.  It'll scan your system and then bring up a windows like this...

[IMG]http://i80.photobucket.com/albums/j185/Speedwell68/Screenshot-HardwareDrivers.png[/IMG]

You should see a list of available drivers like I have.  You need to select 'Nvidia accelerated graphics driver (version 173)' and click the 'Activate' button. You will need to re-start your PC to complete the install.  If that doesn't work come back to this thread and we will see what else needs to be done.

---

### Post by Bartender on 2010-01-07
Once you've downloaded/installed the nVidia drivers, you'll see "nVidia X Server Settings" in Administration drop-down.  But if you just go into that icon, any changes you make may not be saved.  There's a trick to get around that.  Open a terminal and type in 

```
gksudo nvidia-settings
```

Which puts you into the nVidia X Server Settings.  The GUI looks the same as if you just clicked on the icon in Administration drop-down, but the difference is when you click on "Save to X Configuration" the changes will actually be saved.

---

