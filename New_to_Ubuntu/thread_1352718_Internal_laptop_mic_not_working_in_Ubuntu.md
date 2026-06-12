---
title: "Internal laptop mic not working in Ubuntu"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by janderson91z on 2009-12-11
Hey guys. I recently installed Ubuntu 9.10 on my Sony Vaio VPCCW17FX and my sound works fine. Audio output and input ports work. My internal mic that's beside my camera doesn't work. After battling with getting my Nvidia drivers to work (screen would be blank when i restarted, had to tell the xconf file to see my monitor) this is the only thing that's not working. Any help would be great. Thanks.

---

### Post by kmac on 2009-12-12
> **janderson91z said:**
> Hey guys. I recently installed Ubuntu 9.10 on my Sony Vaio VPCCW17FX and my sound works fine. Audio output and input ports work. My internal mic that's beside my camera doesn't work. After battling with getting my Nvidia drivers to work (screen would be blank when i restarted, had to tell the xconf file to see my monitor) this is the only thing that's not working. Any help would be great. Thanks.

Please post results of 

```
$ lspci
$lsusb
```

---

### Post by Driftu on 2009-12-12
> **kmac said:**
> Please post results of 

```
$ lspci
$lsusb
```

me too not work in HP DV6-1223

ubuntu@ubuntu-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
08:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ubuntu@ubuntu-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0408:03f1 Quanta Computer, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by janderson91z on 2009-12-12
> **kmac said:**
> Please post results of 

```
$ lspci
$lsusb
```

```
justin@justin-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a74 (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be3 (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 SD Host controller: Ricoh Co Ltd Device e822
04:00.1 System peripheral: Ricoh Co Ltd Device e230
04:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832
04:00.4 SD Host controller: Ricoh Co Ltd Device e822
```
```
justin@justin-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:18b5 Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by janderson91z on 2009-12-14
Hey guys. I'm sorry to bump this thread but I'm curious if anyone knows of a solution for me? I often use Skype on the go and having my internal mic working would be beneficial.

Thanks.

---

### Post by ukripper on 2009-12-14
ok in terminal type this command ```
alsamixer
``` and make sure all options have bars raised to 100%. Then we go from there

---

### Post by janderson91z on 2009-12-14
> **ukripper said:**
> ok in terminal type this command ```
alsamixer
``` and make sure all options have bars raised to 100%. Then we go from there

Done.

Both of the mic ones were actually all the way down. What doesn't make sense to me is that even before and after, if I'm in the audio preferences and tap on the mic, the level bar goes up and down. Nothings muted but yet it still doesn't work in Skype or anything.

---

### Post by ukripper on 2009-12-15
ok can you right click on volume icon in your panel and open volume control

Then .. just click  PREFERENCES and check on CAPTURE and DIGITAL and DIGITAL INPUT SOURCE.

After you done the  steps above go back to main Volume control window, NEW TAB should have appeared, just click on it (it shows DIGITAL INPUT SOURCE) and change the value to DIGITAL MIC 

Try this if it works.

---

### Post by janderson91z on 2009-12-16
> **ukripper said:**
> ok can you right click on volume icon in your panel and open volume control

Then .. just click  PREFERENCES and check on CAPTURE and DIGITAL and DIGITAL INPUT SOURCE.

After you done the  steps above go back to main Volume control window, NEW TAB should have appeared, just click on it (it shows DIGITAL INPUT SOURCE) and change the value to DIGITAL MIC 

Try this if it works.
 
I don't see a digital input source.

---

### Post by ukripper on 2009-12-16
> **janderson91z said:**
> I don't see a digital input source.

what options you see there?

---

### Post by janderson91z on 2009-12-16
> **ukripper said:**
> what options you see there?

"Internal Audio (1 output/1 input) Analog Stereo Input"

"Internal Audio (1 input) Analog Stereo Input"

"Internal Audio (1 output) Analog Stereo Output"

That is the 3 profiles I see under the Sound Preferences. I beleive you're layout is a bit different. I think 9.10 changed the Sound Preference layout around. I hope that's the information you're looking for. Thanks for continuing to help me.

---

### Post by callan79 on 2009-12-16
> **janderson91z said:**
> Both of the mic ones were actually all the way down. What doesn't make sense to me is that even before and after, if I'm in the audio preferences and tap on the mic, the level bar goes up and down. Nothings muted but yet it still doesn't work in Skype or anything.


Hiya,

This may or may not be relevant, but something strange I found today.

I helped a friend move from the Windows world, to the Ubuntu world on her new EeePC Netbook.

Everything worked, except Skype. No webcam, but this is pretty common. There was also no audio from internal Mic.

I checked the volume control, everything looked OK. I installed the 'pavumeter' package, ran it, and the meters bounce up and down when we made noise (clapped hands, etc).

But in Skype - no Audio, just a background noise.

Tried loading Sound Recorder (from the Applications >> Sound & Video menu), this recorded perfectly.

So it's just Skype.

Next was to get into volume control, and unlock the recording controls so I could adjust left and right volume independently. I moved right volume to zero, and left volume to 75%. Sound instantly worked. This was in the more advanced volume control, which I had to install (pavucontrol) and then start from the Applications menu.

Did you want to try this?

Cheers
Callan

---

### Post by janderson91z on 2009-12-16
Hi Callan.

I installed said app. I tried the Sound Recorder before, I only got noise, same with Skype. I did exactly what you said you tried. The levels were jumping up and down when I made noises but unfortunately that didn't solve the problem. Now I just get less noise haha. Thanks for the suggestion though.

---

### Post by kristiang on 2010-08-01
> **janderson91z said:**
> I don't see a digital input source.

I  had the same issue on my netbook Samsung N130 with Ubuntu NE 10.04 LTS  and in the system>preferences>sound I just uncheck the mute  checkbox on the 'input' tab like in the picture below:  [http://www.flickr.com/photos/52642733@N06/4850737285](http://www.flickr.com/photos/52642733@N06/4850737285)

---

