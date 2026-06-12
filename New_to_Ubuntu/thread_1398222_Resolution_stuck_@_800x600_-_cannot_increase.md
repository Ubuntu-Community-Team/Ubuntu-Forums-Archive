---
title: "Resolution stuck @ 800x600 - cannot increase"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by faraz_k86 on 2010-02-04
I just installed ubuntu on this old P3 system of mine, everything went smoothly but the resolution is a problem, its set at 800 x 600 and it cannot be increased.

I checked from Preferences>> Display and 800x600 is the maximum available.

how can i set it higher?

Here is the hardware list of this system:

```
H/W path           Device      Class       Description
======================================================
                               system      Deskpro
/0                             bus         0684h
/0/1                           memory      128KiB BIOS
/0/5                           processor   Pentium III (Coppermine)
/0/5/6                         memory      32KiB L1 cache
/0/5/7                         memory      256KiB L2 cache
/0/21                          memory      System Memory
/0/21/0                        memory      128MiB DIMM SDRAM Synchronous 133 MHz (7.5 ns)
/0/21/1                        memory      DIMM SDRAM Synchronous [empty]
/0/21/2                        memory      128MiB DIMM SDRAM Synchronous 133 MHz (7.5 ns)
/0/22                          memory      Flash Memory
/0/22/0                        memory      512KiB Chip FLASH Non-volatile
/0/0                           memory      
/0/2                           memory      
/0/100                         bridge      82815 815 Chipset Host Bridge and Memory Controller Hub
/0/100/1                       bridge      82815 815 Chipset AGP Bridge
/0/100/1/0                     display     NV11 [GeForce2 MX/MX 400]
/0/100/1e                      bridge      82801 PCI Bridge
/0/100/1e/8        eth0        network     82801BA/BAM/CA/CAM Ethernet Controller
/0/100/1f                      bridge      82801BA ISA Bridge (LPC)
/0/100/1f.1        scsi0       storage     82801BA IDE U100 Controller
/0/100/1f.1/0      /dev/sda    disk        10GB ST310212A
/0/100/1f.1/0/1    /dev/sda1   volume      9303MiB EXT4 volume
/0/100/1f.1/0/2    /dev/sda2   volume      462MiB Extended partition
/0/100/1f.1/0/2/5  /dev/sda5   volume      462MiB Linux swap / Solaris partition
/0/100/1f.1/1      /dev/cdrom  disk        SCSI CD-ROM
/0/100/1f.4                    bus         82801BA/BAM USB Controller #1
/0/100/1f.5                    multimedia  82801BA/BAM AC'97 Audio Controller
```

---

### Post by Grenage on 2010-02-04
I have a guide [here]("http://www.grenage.com/xorg.html") that should cover what you need.  Post back if not.

---

### Post by faraz_k86 on 2010-02-04
thx for the post but i did everything till te cvt part and it made no change.. the cvt looked too advanced and it was also a pain to read that amount of text on this resolution.. is there any simpler method?

---

### Post by Grenage on 2010-02-04
Not that I am aware of, unfortunately.  The *cvt* part is what will likely make the difference.

I don't know if the GeForce2 MX/MX 400 is supported in the current nvidia drivers, are you using "nv" as the driver in xorg.conf?

---

### Post by realzippy on 2010-02-04
[http://packages.ubuntu.com/de/intrepid/nvidia-glx-96](http://packages.ubuntu.com/de/intrepid/nvidia-glx-96)

according to the wiki the card is supported by:

nvidia-glx-96

although it is not listed on NVIDIA's download page....

---

### Post by Grenage on 2010-02-04
Ah touché, they seem to list it under *legacy*. [http://www.nvidia.co.uk/object/linux_display_ia32_100.14.11_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_100.14.11_uk.html)

---

### Post by superprash2003 on 2010-02-04
take a look under system->admin->hardware drivers incase any graphic card drivers are available

---

### Post by faraz_k86 on 2010-02-05
thanks guys but none of it seems to be working.. I tried the hardware drivers via system>>admin and there was a driver there recommended for my system.. but when i installed it cause even more problems.. now my desktop is set at a low rersolution of 640x480 and cannot be increased..

i tried downloading the driver file from the link given abouve, it is a .run file and they explain how to run it..

this is wat i did, i downloaded the .run file to the desktop and then via terminal wrote: cd ~/Desktop and then sh NVIDIA-Linux-x86-100.14.11.pkg1.run but that gives an error of cannot run or something..


any suggestions?

---

### Post by Grenage on 2010-02-05
> thanks guys but none of it seems to be working.. I tried the hardware drivers via system>>admin and there was a driver there recommended for my system.. but when i installed it cause even more problems..

Ok, let's work off the basis that the Nvidia driver installed via *hardware drivers* is running (bad resolution aside).  Run this:

```
sudo apt-get install nvidia-settings
```

Once installed, run it:

```
gksu nvidia-settings
```

Can you get the res you need using the nvidia panel?

---

### Post by faraz_k86 on 2010-02-05
k i tried that.. the nvidia settings opened up but even there the maximum resolution was 640 x 480

---

### Post by Grenage on 2010-02-05
Ok, can you post your monitor make and model, along with your desired resolution?

---

### Post by Jackzor on 2010-02-05
I swear its drivers.

---

### Post by faraz_k86 on 2010-02-05
my monitor is good, it worked perfectly under windows xp

my monitor is viewsonic 17PS and the resolution id like is 1024x768

---

### Post by Grenage on 2010-02-05
Any joy with this one?

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Viewsonic"
	ModelName "17PS"
	HorizSync 30 - 86
	VertRefresh 50 - 160
        Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nvidia"
	VendorName "Nvidia"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection
```

---

### Post by faraz_k86 on 2010-02-05
thx a lot for your help guys but the resolution is fixed now..

i just threw away the problematic nvidia card and amd using the build in intel display chip..

it wont run compiz or anything but atleast i got the proper resolution.

thx a lot for your help so far :)

---

### Post by faraz_k86 on 2010-02-05
> **Grenage said:**
> Any joy with this one?

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Viewsonic"
	ModelName "17PS"
	HorizSync 30 - 86
	VertRefresh 50 - 160
        Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nvidia"
	VendorName "Nvidia"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection
```

Thank you grenage, for this dedicated kind of support :)
ill be sure to try this if i want plan on using nvidia back.

---

### Post by Grenage on 2010-02-05
Glad you got it working, one way or the other :)

---

