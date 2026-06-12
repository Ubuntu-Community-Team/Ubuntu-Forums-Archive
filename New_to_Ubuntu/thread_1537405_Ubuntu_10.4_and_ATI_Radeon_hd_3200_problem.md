---
title: "Ubuntu 10.4 and ATI Radeon hd 3200 problem"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by mattweed9 on 2010-07-23
yes I have searched, but I give up and I am now asking for help.

I have a ATI Radeon hd 3200 mobility chip-set and the proprietary driver offered in the Hardware Drivers tool do not seem to work correctly. When I install them, the boot screen in enlarged and distorted and when I try to run playonlinux I get a error message that 3d acceleration is not enabled. Maybe these are two different problems, I am not sure.

Any help would be great, or a point in the right direction even. I  have spent the last three days, when I have free time, trying to figure this out and I am burnt out. Sadly, everything worked fine Karmic and I can't seem to figure out what the problem is.

Gateway nv52-14
AMD Athlon 64 x2 ql-64
ATI Radeon hd 3200 mobility
Running ubuntu 10.4 64 bit

Video Card info
> 01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]

And some extra info just in case.
> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
	Kernel modules: shpchp
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
	Kernel driver in use: ohci_hcd
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
	Kernel driver in use: ohci_hcd
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
	Kernel driver in use: ehci_hcd
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
	Kernel driver in use: ohci_hcd
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
	Kernel driver in use: ohci_hcd
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
	Kernel driver in use: ehci_hcd
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
	Kernel modules: amd64_edac_mod
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
	Kernel driver in use: radeon
	Kernel modules: radeon
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
	Kernel driver in use: tg3
	Kernel modules: tg3
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Kernel driver in use: ath9k
	Kernel modules: ath9k
mobile@mobile:~$ 


---

### Post by corrytonapple on 2010-07-23
Although I don't know much about Graphics, you said Ubuntu 10.4. That is a beta version and is still in testing. Is it 10.04? Please clarify.

---

### Post by mattweed9 on 2010-07-23
I was under the impression that the Ubuntu 10.4 LTS release was final, not a Beta. And yes, I am using Ubuntu 10.4 LTS 64 bit desktop.

Edit: I have also un-installed the proprietary driver three times to make sure it wasn't just a bad install. I can get 1366x768 resolution on my desktop which is what it should be, but everything just seems a little sluggish when I have it installed.

edit: I un-installed playonlinux newest version and used the one from the software center, I haven't gotten the error message yet, but haven't tried a game and don't have time too right now. I will try later when I get home from work.

Also, with out the hardware drivers driver installed, the boot screen looks like I imagine it should. If everything else is as should be I can live with that, but just doesn't seem right with the whole system running a little slower and all.

---

### Post by clhsharky on 2010-07-23
mattweed9

1
>  I am using Ubuntu 10.4 LTS 64 bit 
Incorrect, that would indicate the 40th month of 2010.
Ubuntu 10.04 LTS would be correct.
2
Did you upgrade or fresh install from Karmic?
3
The radeon OSS driver and ATI blob both have 3D acceleration for your chip.
Use these instructions to remove fglrx to get back to default settings.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
Then install ATI cat correctly.

Sharky

Radeon default OSS driver has had better 2D acceleration than fglrx for a while now, and fglrx is far superior to radeon for 3D which you will need for your IGP chip to run window apps with wine in Linux.
ATI Catalyst 10.7 will be out Monday. The newest cats has better 2D acceleration than the previous cats.

---

### Post by mattweed9 on 2010-07-23
Thanks lol. I stand corrected, I am using 10.04.

I did a fresh install, and I installed it twice. Once three days ago, and another clean install yesterday thinking maybe it was a installation error. 

As for what you mentioned,I will try that and post a update. 

Thanks for time and the help.

Edit:
Okay so I restored everything back to default and reinstalled the driver from the hardware drivers tool again and same thing. Is there a better " correct way" then that?

---

### Post by QIII on 2010-07-23
After you installed the driver, did you run the following in the terminal (Applications | Accessories | Terminal)

```
sudo aticonfig --initial
```

?

You will be prompted for your password.  That is your normal login password.  Type it in, but be aware that nothing will appear on the screen.

---

### Post by mattweed9 on 2010-07-23
This is the message I got with the above command

> Found fglrx primary device section
 Unable to find any supported Screen sections


---

### Post by mattweed9 on 2010-07-24
here is my xorg.conf if this helps

> Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

Also, I ran the system test tool and the 3d gears appears and other test seem to work, but I still can't figure out way the boot loader screen is still distorted. Could it be that the drivers are installed correctly, but some how the default resolution setting for the loader are some how getting changed?

---

### Post by QIII on 2010-07-24
The "boot screen" issue is known.  

If you are saying the graphics you saw on boot up were crisp and nice  looking until you installed the ATI driver (and this happens also with  NVIDIA) and then became pixellated, this is a known issue with  plymouth.  There are work arounds, but they require some changes to  configuration files that I simply don't think are worth the effort to  make something pretty for the 5 or 6 seconds that I see it.

Karmic used xsplash instead of plymouth, so this simply didn't exist.

This will be resolved eventually, so I am content to wait.

I'm more interested in the playonlinux issue.

But first...

We can try looking at some 3D effects in something like compiz.  Do you have it installed?

---

### Post by mattweed9 on 2010-07-24
I un-installed the newest version of playonlinux and used the one from the Software Center, and I now no longer receive that message. So it seems in short, that basically I spent three days trying to fix something that wasn't broken at all. I was assuming that the boot loader problem and the one with the playonlinux just had to be a graphics driver error.



Thanks for clearing these things up and getting rid of the head ache all of this was giving me.  I didn't want to really tweak anything else or place anything else on the drive until I had this resolved.

---

### Post by ravisghosh on 2010-08-22
> **mattweed9 said:**
> This is the message I got with the above command

I'm having the same issue on installing ATI Catalyst 10.7 but I dont have playonlinux installed.

---

### Post by corrytonapple on 2010-08-22
> **ravisghosh said:**
> I'm having the same issue on installing ATI Catalyst 10.7 but I dont have playonlinux installed.
Please start a new thread so answers don't get mixed.

---

### Post by whangway on 2010-11-08
ubuntu 10.4 crashes after I installed the ati hd3200 driver

---

