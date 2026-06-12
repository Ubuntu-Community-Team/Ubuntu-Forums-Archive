---
title: "Total Newbie with a HP G62 (G62-208CA) laptop"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by mannyweb.ca on 2010-08-09
This being my first post I'd like to say to everyone and congratulate those that make the transition from Windows to Ubuntu and easier experience.

Second if a post like mine has already been created please feel free to close this thread and redirect me to the proper thread.

So with that out of the way, about two weeks ago I purchased a new laptop specifically the HP G62-208CA, spec are  the following:

- AMD Athlon || Dual-Core Processor P320 (2.1GHz, 1MB L2 Cache)
- 15.6" diagonal High Definition HP BrightView LED Display (1366x768)
- 320GB (7200RPM) Hard Drive
- 3072MB DDR3 SDRAM (2 Dimm)
- 802.11 b/g/n WLAN
- LightScribe Super Multi 8X DVD+RW with Double Layer Support
- 6-Cell 47Whr Lithium-Ion Battery
- AMD M880G with ATI Mobility Radeon HD 4250 Graphics
- 5-in-1 Digital Media Reader


Once I got it home I immediately installed Ubuntu 10.04 (64-bit).  A full install  no halfway cowardly dual boot with windows, I just threw myself into the Ubuntu world.  Overall my experience has been great, I've most things working out of the box and installed Compiz Fusion and got all the eye candy and stuff working.

The only thing I've had issues with is audio.  I've updated the ALSA to version 1.0.23 and got the audio working, but every once in a while my internal mic goes to hell and my audio settings along with it.  

Here are my audio settings in my Sound Preferences are:

Hardware shows 2 devices to configure  Internal Audio which is set to Analog Stereo Duplex and RS880 Audio Device [Radeon HD 4200] set to Digital Stereo (HDMI) Output.

Input shows only 1 device which is Internal Audio Analog Stereo which ofcourse is selected.

Output show 2 devices; Internal Audio Analog Stereo which is the one selected and RS880 Audio Device [Radeon HD 4200]. 

This is the setup that works anything I change and everything stops working.  So is there anything I can do to get this to work or is it just a matter of tough luck and hope this will get fixed down the road.

Thanks to all beforehand.

---

### Post by mannyweb.ca on 2010-08-09
I'd also like the add that the internal mic works only until you use it, in others after one you it goes to hell and then only a reboot will bring it back to life.  Doesn't matter what program either, could be Sound Recorder, over Empathy, making a video on Facebook or Livestreaming through TwitCam whatever it is it kills the internal mic settings and then I'm forced to reboot once again.  :(

---

### Post by Sulton Majnoon on 2010-08-14
I just picked up the same laptop and have been setting it up for the passed hour.  I noticed the audio worked for a bit then died.  Will be investigating after I get the wireless working. :D

---

### Post by nix-idioteque on 2010-08-15
I can't seem to get my wireless card to work either...  Strange

---

### Post by sandyd on 2010-08-15
> **mannyweb.ca said:**
> This being my first post I'd like to say to everyone and congratulate those that make the transition from Windows to Ubuntu and easier experience.

Second if a post like mine has already been created please feel free to close this thread and redirect me to the proper thread.

So with that out of the way, about two weeks ago I purchased a new laptop specifically the HP G62-208CA, spec are  the following:

- AMD Athlon || Dual-Core Processor P320 (2.1GHz, 1MB L2 Cache)
- 15.6" diagonal High Definition HP BrightView LED Display (1366x768)
- 320GB (7200RPM) Hard Drive
- 3072MB DDR3 SDRAM (2 Dimm)
- 802.11 b/g/n WLAN
- LightScribe Super Multi 8X DVD+RW with Double Layer Support
- 6-Cell 47Whr Lithium-Ion Battery
- AMD M880G with ATI Mobility Radeon HD 4250 Graphics
- 5-in-1 Digital Media Reader


Once I got it home I immediately installed Ubuntu 10.04 (64-bit).  A full install  no halfway cowardly dual boot with windows, I just threw myself into the Ubuntu world.  Overall my experience has been great, I've most things working out of the box and installed Compiz Fusion and got all the eye candy and stuff working.

The only thing I've had issues with is audio.  I've updated the ALSA to version 1.0.23 and got the audio working, but every once in a while my internal mic goes to hell and my audio settings along with it.  

Here are my audio settings in my Sound Preferences are:

Hardware shows 2 devices to configure  Internal Audio which is set to Analog Stereo Duplex and RS880 Audio Device [Radeon HD 4200] set to Digital Stereo (HDMI) Output.

Input shows only 1 device which is Internal Audio Analog Stereo which ofcourse is selected.

Output show 2 devices; Internal Audio Analog Stereo which is the one selected and RS880 Audio Device [Radeon HD 4200]. 

This is the setup that works anything I change and everything stops working.  So is there anything I can do to get this to work or is it just a matter of tough luck and hope this will get fixed down the road.

Thanks to all beforehand.
can you post the ouput of
```

aplay -l
lspci
```

---

### Post by mannyweb.ca on 2010-08-16
> **carlee said:**
> can you post the ouput of
```

aplay -l
lspci
```

Sure.



```
List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```


Also about a week ago my webcam stopped working in a really strange way it gets detected, but it seems that every application thinks my webcam is being used by another application.  ](*,)

---

### Post by sandyd on 2010-08-17
try installing pulseaudio

---

### Post by mannyweb.ca on 2010-08-21
^ Thanks but nothing changes.  It's something between my webcam and audio.  Cause everytime I try to use it everything goes to hell.  It doesn't matter what program it could be Cheese, Facebook, Twitcam whatever my webcam freezes and my audio goes nuts.

Here is this lsusb thing ijf anybody can figure it out, many thanks again.

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b1aa Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by Jan051 on 2010-08-22
Hi, I have an sort of offtopic question:
Can you confirm that ATI's proprietary drivers work fine on the ATI mobility radeon HD 4250? I'm having a hard time finding information about that. Thanks in advance!;)

---

### Post by mannyweb.ca on 2010-08-30
>  **Avahi will always start even if a .local domain is present**

   The avahi-daemon package, which implements the mDNS "zeroconf" standard, formerly included a check to avoid running when a conflicting .local DNS domain is present, as it was reported that some ISPs advertise such a .local domain on their networks, leaving Ubuntu hosts unable to see names advertised on the local network ([327362]("https://bugs.launchpad.net/bugs/327362")).  In Ubuntu 9.10, avahi-daemon is started regardless. 
 It  is possible that this may cause other problems.  If your network is  configured this way, you can disable mDNS using the following command: 
 
 sudo stop avahi-daemon
sudo sed -e '/^start/,+1s/^/#/' /etc/init/avahi-daemon.conf 

Got this from this website.  

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

---

### Post by jayrod422 on 2010-10-10
I've tried the latest ATI drivers (Catalyst 8.771) for my Radeon HD 4250 and cant get things to work.

fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15

dmesg | grep fglrx
[    9.782833] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    9.880467] [fglrx] Maximum main memory to use for locked dma buffers: 3546 MBytes.
[    9.880505] [fglrx]   vendor: 1002 device: 9715 count: 1
[    9.880799] [fglrx] ioport: bar 1, base 0xb000, size: 0x100
[    9.881091] [fglrx] Kernel PAT support is enabled
[    9.881104] [fglrx] module loaded - fglrx 8.77.5 [Aug 25 2010] with 1 minors
[    9.906593] [fglrx:__mc_heap_map_virtual_space] *ERROR* Failed to map the virtual space
[    9.906596] [fglrx:mc_heap_alloc_reserved_mem] *ERROR* Can not get virtual address for this reserved range
[    9.906598] [fglrx:MCIL_AllocateMemory] *ERROR* Can not allocate requested local FB memory 
[    9.906601] [fglrx:__gart_init] *ERROR* Gps_GartInitialization failed.
[    9.906602] [fglrx:gal_init] *ERROR* Failed to initialize gal
[    9.906604] [fglrx:mc_heap_init] *ERROR* Fail to initialize GAL
[    9.906605] [fglrx:firegl_init_pcie] *ERROR* GAL initialization failure

---

