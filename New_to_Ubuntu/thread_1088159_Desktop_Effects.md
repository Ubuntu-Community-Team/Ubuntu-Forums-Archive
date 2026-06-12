---
title: "Desktop Effects"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by smitty96 on 2009-03-05
Hi, I have a Dell Pentium 4 computer with Win. XP an Ubuntu on it, and I'm having trouble with the Desktop Effects. When I click to enable "normal" desktop effects, it says "searching for drivers", and then it tells me it cannot enable desktop effects. Is there some way around this? I'm not sure what kind of graphics card I have, but I know I can play 3D games in Windows. Thanks in advance.

---

### Post by perlluver on 2009-03-05
Run this command in a terminal, and post the output.  Applications>Accessories>Terminal ```
lspci
``` that will let us know what card you have.

---

### Post by taurus on 2009-03-05
Just run this command from a terminal to see which one you have.  Bet it's one of those Intel integrated graphic controllers.

Applications -> Accessories -> Terminal
```
lspci | grep VGA
```

---

### Post by smitty96 on 2009-03-05
First code shows: [I]00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
02:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
02:0b.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)[/I]
Second code shows: *01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF*
So how do I use desktop effects? They're so cool! :)

---

### Post by 73ckn797 on 2009-03-05
Have you gone to System/Administration/Hardware Drivers, to see if there are any recommended drivers for the video? If so then select it and "activate" it.

---

### Post by smitty96 on 2009-03-05
It says "No proprietary drivers are in use on this system." Do I need to get a driver from somewhere?

---

### Post by brdmb on 2009-03-05
Sorry, but I don't think the advanced desktop effects will work with your video card.

See [http://ubuntuforums.org/showthread.php?t=510606]("http://ubuntuforums.org/showthread.php?t=510606") for some other folks who had your video card and didn't have much luck...

---

### Post by Darkoan on 2009-03-05
I had similar issue trying to activate desktop effects - I had Synaptic Package Manager download a proprietary driver for me (after pressing 'reload' to make SPM look for the right driver, I did this process 2 or 3 times) and install it and reboot - and it worked fine.

But I have a half decent grpahics card ATI 4800 series - maybe yours wont - that is something youll have to look up.

Sorry Im a newbie too.

---

### Post by smitty96 on 2009-03-06
> **brdmb said:**
> Sorry, but I don't think the advanced desktop effects will work with your video card.

I was just trying to enable normal, not advanced. I doubt advanced will work with my computer.

---

### Post by avtolle on 2009-03-06
I don't think "normal" desktop effects will work with your card; I've the same card, and (while I neither use nor want to use the effects) I've never had them work.

---

