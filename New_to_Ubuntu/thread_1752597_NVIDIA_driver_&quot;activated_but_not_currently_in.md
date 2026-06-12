---
title: "NVIDIA driver &quot;activated but not currently in use&quot;"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by dinostabOMG on 2011-05-08
The proprietary driver: How do I get it to be in use?

This is a fresh install of 11.04 on a brand new Dell XPS 15 L502X.

As far as I can tell I have no hardware acceleration, can't switch to compiz at the moment.

---

### Post by Hedgehog1 on 2011-05-08
I think the message is incorrect.  It says that for my NVidia driver too, and I an getting 3d acceleration and audio over HDMI (which requires the driver be active to work).

You can use Compiz in the way you want using 'Ubuntu Classic' UI: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")

You will need to load CCSM from the Ubuntu Software Center to turn on the cube and wobbly windows.

Hope this Helps...

***The Hedge***

p.s. Unity uses Compiz - so if you see Unity, Compiz is functioning.

:KS

---

### Post by powerpleb on 2011-05-08
I get that too and my 3d works. I read somewhere that it is because Natty is now using the open source Nouveau drivers instead of NVidia's proprietary ones.

Not sure how true that is.

---

### Post by yetiman64 on 2011-05-08
> **powerpleb said:**
> I get that too and my 3d works. I read somewhere that it is because Natty is now using the open source Nouveau drivers instead of NVidia's proprietary ones.

Not sure how true that is.

My Natty install with the proprietary drivers enabled/installed also shows the warning, even when the effects all work ok. I think that warning may be a bug, though haven't looked further into it.

---

### Post by powerpleb on 2011-05-08
Yeah, but do the effects work because of the FOSS Nouveau drivers or because of the NVidia ones?

---

### Post by yetiman64 on 2011-05-08
> **powerpleb said:**
> Yeah, but do the effects work because of the FOSS Nouveau drivers or because of the NVidia ones?

Good question. I'll have to look into blacklisting the nouveau drivers next time I boot up Natty. Thanks for the tip.

---

### Post by CaptainMark on 2011-05-08
i have a GE Force 9400 GT and the foss drivers dont work for me yet, the nouveau drivers are in early days though, more cards are being supported all the time but i doubt they will ever reach the standard of the propietary one for obvious reasons

---

### Post by nasul on 2011-05-08
> **dinostabOMG said:**
> The proprietary driver: How do I get it to be in use?

This is a fresh install of 11.04 on a brand new Dell XPS 15 L502X.

As far as I can tell I have no hardware acceleration, can't switch to compiz at the moment.

It's a Optimus Laptop and because of that only the Intel HD will work under Linux. So it was for me. Under Windows 7 it will work but who uses Windows.

---

### Post by kitsuneclem on 2011-05-08
> **nasul said:**
> It's a Optimus Laptop and because of that only the Intel HD will work under Linux. So it was for me. Under Windows 7 it will work but who uses Windows.
My brother the windows Geek

any ways IT must be a bug cause it didnt say that for me I was able to Install MY Nvidia propriety driver with out issue, may want to submit a bug report :)

---

### Post by spikoley on 2011-05-08
It is a [bug]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788").  Check under Additional Drivers for this message, "This driver is activated but not currently in use".  Make sure you update the bug to let them know it is widespread.

---

### Post by rosencrantz on 2011-05-08
The official Nvidia drivers don't support Optimus setups under Linux. You can install the proprietary drivers, but your desktop will run on the Intel chip.

---

### Post by dinostabOMG on 2011-05-09
I'm pretty sure it's correct, I am not getting 3d acceleration. If I try to run compiz --replace it fails and falls back to metacity. My transparent terminal background is the desktop, not real transparency.

nasul and rosencrantz - are you telling me there's nothing I can do? Can I blacklist the FOSS drivers and use the proprietary ones anyway? Is there some other way to get 3d graphics working?

Kitsuneclem - you have the same setup as me?

---

### Post by roads637 on 2011-08-10
I am having the same problem. this driver is activated but not currently in use 
running ubuntu 11.04 on an asus UL50VT

---

### Post by yetiman64 on 2011-08-11
> **roads637 said:**
> I am having the same problem. this driver is activated but not currently in use 
running ubuntu 11.04 on an asus UL50VT

> **spikoley said:**
> It is a **[bug]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788")**.  Check under Additional Drivers for this message, "This driver is activated but not currently in use".  Make sure you update the bug to let them know it is widespread.

If you have compiz working ok or the Unity desktop working the driver **is** in use. There is a bug in the jockey-gtk package in 11.04 that reports that even when the driver is used. Do you have a problem with using the Unity interface or any 3d effects appart from that error reported in "Additional Drivers" (aka jockey-gtk) ?

Here is the full bug link from spikoley's post :[COLOR=Blue][COLOR=Black][https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788) Cheers, yetiman64.
 [/COLOR]
[/COLOR]

---

### Post by venik212 on 2011-08-11
I have the same problem with an NVIDIA Riva TNT 2 (an older graphics card) which produced high graphics resolution under XP but under UBUNTU can do only 1024X 768.  When I tried sudo apt-get install nvidia-current and sudo nvidia-xconfig and rebooted, the GUI never came up until I removed the xorg.conf that was created by invoking the nvidia-xconfig.  I am a bit lost here.  What should the xorg.conf contain in its DEVICE section for this to work properly?  I got Unity 2-D to work, but I would like to get the full resolution the card can produce.

---

### Post by yetiman64 on 2011-08-12
> **venik212 said:**
> I have the same problem with an **NVIDIA Riva TNT 2** (an older graphics card) which produced high graphics resolution under XP but under UBUNTU can do only 1024X 768.  When I tried sudo apt-get install nvidia-current and sudo nvidia-xconfig and rebooted, the GUI never came up until I removed the xorg.conf that was created by invoking the nvidia-xconfig.  I am a bit lost here.  What should the xorg.conf contain in its DEVICE section for this to work properly?  I got Unity 2-D to work, but I would like to get the full resolution the card can produce.

nvidia-current supports ge-force 6 series and later cards, you may need to download a "legacy" driver from the [[COLOR=Blue]--nvidia website--[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us") (use option 1 and search for "legacy" and "TNT and TNT2 Series" and "Linux ?? bit") for support for a TNT2 card. When you use the search, check the Additional Information tab for instructions/notes etc.

From [[COLOR=Blue]--here--[/COLOR]]("http://packages.ubuntu.com/natty/nvidia-current") (packages.ubuntu.com/natty/nvidia-current)
> **NVIDIA binary Xorg driver, kernel module and VDPAU library**

      The binary driver provide optimized hardware acceleration of OpenGL applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out and flat panel displays are also supported. 

 This package also includes the source for building the kernel module required by the Xorg driver, and provides NVIDIA's implementation of the Video Decode and presentation API. The latter enables acceleration for GeForce 8 and later series cards for h264 video. 

 **GPUs such as GeForce series 6 or newer are supported. **

 See /usr/share/doc/nvidia-current/README.txt.gz for a complete list of supported GPUs and PCIIDs    
**Edit:** alternatively, you could get the driver number from this site and check the repositories for a corresponding nvidia-glx-??? driver instead of using the drivers from the nvidia site.

---

