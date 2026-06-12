---
title: "how do I determine what graphics driver I have?"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by s1baker on 2010-11-27
My system:
10.10 32 bit, AMD 64 chip, desk-top.
---------------------------

I would like to install the latest graphics driver for my system and I am trying to find out what driver to get. I think it is nVidia, but not sure.
Typing lspci in the terminal brings up a list of about 20 things, most of them nVidia, but I noticed these two lines:
03:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
03:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

My board is a GeForce 6100-M9. I went to the nVidia website and downloaded this file for that board:
 NVIDIA-Linux-x86-260.19.21.run
but I still don't know if it is the correct one.


Some other things:
-My display works just fine right now, except I wish it was a little brighter... monitor brightness is up all the way and I can't brighten it any farther. I think I might need the proprietary drivers.  

-I think I have the generic driver in my system now as I don't have a file called Xorg in the etc/X11 directory, but not sure.

---

### Post by bwhite82 on 2010-11-27
Can you post the full output of lspci here?

---

### Post by Quackers on 2010-11-27
Go to System > Admin > Hardware drivers (or Additional Drivers). That will tell you whether any new drivers are available for your card.

---

### Post by sikander3786 on 2010-11-27
Seems like your graphics card is ATI Radeon.

> 03:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

Check under Additional Drivers as **Quackers** mentioned above but I don't think drivers for X300 are available for Maverick.

You'll have to depend on the default drivers that come with Maverick.

Or try this.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by jmszr on 2010-11-27
Never mind, thought he needed the nVidia driver version #.

---

### Post by wojox on 2010-11-27
```
lspci | grep VGA
```

---

### Post by s1baker on 2010-11-27
here is the readout from lspci:
------------------------------------------------------------------
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
03:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
04:08.0 Modem: SILICON Laboratories Intel 537 [Winmodem] (rev 04)
------------------------------------------------------------------

Also System/Administration/Additional Drivers did not show anything.

and lspci | grep VGA shows this:

03:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

---

### Post by wojox on 2010-11-27
ATI has dropped support for all RV200-500 cards starting with 9.4 and future drivers for Linux and Windows.

I'd check out sikander3786's link.

---

### Post by s1baker on 2010-11-27
doing this in the terminal:
lspci | grep VGA
shows this:
ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

----------------------------------------
this website:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

has this in it's listing:
"Accelerated 3D support (r300, r400 and r500 series)"
"All these cards and derivatives have good 3D acceleration support :"
:X300 / rv370 based cards"
-------------------------------------------


Does this mean that there is a open source driver for my card, or
is the driver noted on the webste the one I already have?

---

### Post by wojox on 2010-11-27
I've never had an ATI Card/Chip. I would look into reading this [Removing the proprietary fglrx driver]("https://help.ubuntu.com/community/RadeonDriver#Removing%20the%20proprietary%20fglrx%20driver")

---

### Post by WienerWuerstel on 2010-11-27
> **s1baker said:**
> doing this in the terminal:
lspci | grep VGA
shows this:
ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

----------------------------------------
this website:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

has this in it's listing:
"Accelerated 3D support (r300, r400 and r500 series)"
"All these cards and derivatives have good 3D acceleration support :"
:X300 / rv370 based cards"
-------------------------------------------


Does this mean that there is a open source driver for my card, or
is the driver noted on the webste the one I already have?

There is a Open Source Driver available for your Card and you probably already use it.

Enter the Commands *sudo apt-get install mesa-utils* and *glxinfo | grep OpenGL* in your Terminal and tell me what Output you get.

---

### Post by s1baker on 2010-11-27
glxinfo | grep OpenGL gives me this read out:

------------------------------------------
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RV380 5B60) 20090101 x86/MMX+/3DNow!+/SSE2 TCL DRI2
OpenGL version string: 1.5 Mesa 7.9-devel
OpenGL extensions
---------------------------------------------

---

### Post by bwhite82 on 2010-11-27
I don't have much experience with ATI cards either -- most Linux enthusiasts stick with Nvidia because they provide updated drivers for Linux. But you may not be totally out of luck, here is the ATI page for your driver (note that it is outdated, AMD stopped supporting your video card) but it may provide hardware acceleration.

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

Install it (per their instructions) and check for HW accel with:

glxinfo | grep render

---

### Post by s1baker on 2010-11-27
So far, all that I have been able to deduce from all of this that ATI is the graphics card because of this:

lspci -nn | grep VGA
03:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] [1002:5b60]

but I am still not sure about what the "Radeon X300" means,
and that I may be using the default Ubuntu 10.10 driver that was installed during installation.

You will have to forgive me, for I know next to nothing about graphic cards and drivers.

---

### Post by bwhite82 on 2010-11-27
> **s1baker said:**
> So far, all that I have been able to deduce from all of this that ATI is the graphics card because of this:

lspci -nn | grep VGA
03:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] [1002:5b60]

but I am still not sure about what the "Radeon X300" means,
and that I may be using the default Ubuntu 10.10 driver that was installed during installation.

You will have to forgive me, for I know next to nothing about graphic cards and drivers.

Your video card is a ATI Radeon X300. If you go to Ati.com and search for Linux drivers for your card, you will come to the link I have provided in an earlier post. There, you will find a link for "Installation Instructions".

---

### Post by s1baker on 2010-11-27
Is there anyway of determining what driver I may have now?

---

### Post by bwhite82 on 2010-11-27
> **s1baker said:**
> Is there anyway of determining what driver I may have now?

Ubuntu does not install proprietary drivers by default, so I'm fairly certain you are using a "generic" driver -- much like Windows would use if you installed that. In both cases (Windows and Linux), one would need to go to the manufacturer's website, in your case ATI, and download/install the driver.

You can find exactly which drivers are currently in use by your system by typing the command: lsmod

---

### Post by s1baker on 2010-11-27
lsmod gives me this print out:
--------------------------------------------------
Module                  Size  Used by
nls_utf8                1069  1 
udf                    79366  1 
crc_itu_t               1383  1 udf
binfmt_misc             6599  1 
radeon                825934  2 
snd_intel8x0           25632  1 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
ttm                    56633  1 radeon
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30200  1 radeon
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
drm                   168054  4 radeon,ttm,drm_kms_helper
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
parport_pc             26058  1 
snd                    49006  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                32011  2 ttm,drm
k8temp                  3132  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
i2c_algo_bit            5168  1 radeon
i2c_nforce2             5179  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
sata_nv                19420  0 
pata_amd                8746  3 
forcedeth              49433  0 
floppy                 54311  0 
---------------------------------------------

---

### Post by bwhite82 on 2010-11-27
> **s1baker said:**
> lsmod gives me this print out:
--------------------------------------------------
Module                  Size  Used by
nls_utf8                1069  1 
udf                    79366  1 
crc_itu_t               1383  1 udf
binfmt_misc             6599  1 
radeon                825934  2 
snd_intel8x0           25632  1 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
ttm                    56633  1 radeon
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30200  1 radeon
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
drm                   168054  4 radeon,ttm,drm_kms_helper
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
parport_pc             26058  1 
snd                    49006  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                32011  2 ttm,drm
k8temp                  3132  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
i2c_algo_bit            5168  1 radeon
i2c_nforce2             5179  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
sata_nv                19420  0 
pata_amd                8746  3 
forcedeth              49433  0 
floppy                 54311  0 
---------------------------------------------

You're using the stock 'Radeon' driver. Post the result of one more command:

glxinfo | grep render

If you get not output then you should try downloading the driver from the afformentioned link (follow their instructions) and then re-run glxinfo | grep render command to see if you have rendering (compositing) which is necessary for "Desktop Effects".

BTW, I should mention Linux calls "drivers" "modules", they both mean the same. Hence: lsmod would translate to "List modules". Hope that makes sense.

---

### Post by s1baker on 2010-11-27
glxinfo | grep render:

------------------------------
direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 (RV380 5B60) 20090101 x86/MMX+/3DNow!+/SSE2 TCL DRI2
-------------------------------

---

### Post by bwhite82 on 2010-11-27
> **s1baker said:**
> glxinfo | grep render:

------------------------------
direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 (RV380 5B60) 20090101 x86/MMX+/3DNow!+/SSE2 TCL DRI2
-------------------------------

Great, now see if you can enable desktop effects: Goto (in your menu):

System>Preferences>Appearance>Visual Effects Tab>Click on 'Extra'.

If you get no warning, and you can "jiggle your title bar" (I mean that literally: Click and hold on a window border of any open application and move your mouse back and forth) If it jiggles, then you have desktop effects enabled and you can close this thread, no need to update your driver -- unless perhaps you're a linux gamer (rare).

---

### Post by clhsharky on 2010-11-27
s1baker

You are using the correct driver(r300) with your hardware(rv380 a X300 series card) with 10.10 release.

Are you having a problem?

Sharky

Features for your card.(r300)drivers
[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

---

### Post by s1baker on 2010-11-27
Sorry about the delay in responce, didn't see we had went to page 3, was looking on page 2 last 10 minutes.

Yes I have the jiggly display.

---

### Post by s1baker on 2010-11-27
but I lost my menu, I don't have any panels to reset the display back to no graphic effects.

---

### Post by s1baker on 2010-11-27
never mind last post, got my panels back.

---

### Post by s1baker on 2010-11-27
The reason I wanted to know what module I have now is that I don't want to install the same thing if I find a module from ATI. What I have now is fine except for the brightness. Pictures on webpages are darker than on my XP setup, the dark parts of pictures are hard to see. Other than that I would not want to look for another module for the card.
I have 2 more questions

1) If I find another module and install it and something screws up, is there a way before hand of saving what I have now so that I may revert back to what I have now.

2) ( This may be a dumb question ) My system is this:
I have a box with 2 hard drives on it. One is XP and the other is Ubuntu.
I am switching between the OS's by going into the bios and setting whichever HD I want to boot off. So am I correct in thinking that the drivers that XP uses are on the XP HD and the modules for Ubuntu are on the Ubuntu HD? 
I mean, these drivers/modules aren't on the board chip are they? I don't want to install any modules that would mess up my XP system just yet, as I am gradually transitioning from XP and Ubuntu, still using XP now.

---

