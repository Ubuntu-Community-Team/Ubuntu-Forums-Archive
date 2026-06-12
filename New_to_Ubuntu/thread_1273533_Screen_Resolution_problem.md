---
title: "Screen Resolution problem"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by g_lev on 2009-09-23
Hello,
(I apologize for my bad English)
I've installed Ubuntu 9.04 about 4 days ago.
After the first installation Ubuntu was great, and the screen resolution was perfect.
Then, I've updated the OS and installed vlc MPlayer etc' and when restarting the computer suddenly I get only 960X600 for maximum display.
I've tried to follow some of the explanations about changing the .conf file but none of this seem to work for me.
So I reinstalled Ubuntu but no luck, I get low resolution again.
help :(.

---

### Post by NightwishFan on 2009-09-23
Hello, and welcome.

I would like to ask what your graphics hardware is. There may be a more appropriate driver available for you.

---

### Post by g_lev on 2009-09-23
Hey, and thank you for answering.
My screen is MAG 996PFs.
I also ran lspci and got this (if it's any help):
> 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:08.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
00:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
Another thing I should mention is that when I get the Ubuntu logon screen (the ubuntu logo and the loading line), the resolution is perfect. only after the OS starts it changes to low resolution (maybe it means that Ubuntu still recognize the screen but have some trouble with OS integration ?).
Thank you very much for your help.

---

### Post by LewRockwell on 2009-09-23
we know it sounds crazy but sometimes we just temporarily plug in an additional display device for a quick fix

sure beats hacking on it, not to mention that customers and friends can do that easily at home

.

---

### Post by g_lev on 2009-09-23
> **LewRockwell said:**
> we know it sounds crazy but sometimes we just temporarily plug in an additional display device for a quick fix

sure beats hacking on it, not to mention that customers and friends can do that easily at home

.
I apologize for my bad English once again, but I didn't quite understand what you meant by that.

---

### Post by g_lev on 2009-09-24
can anybody please help me ? :sad:

---

### Post by zeroseven0183 on 2009-09-24
> **g_lev said:**
> I apologize for my bad English once again, but I didn't quite understand what you meant by that.

I think what he means is you look for another monitor, plug it in the CPU to test it.

OR

Have another graphics card installed on your computer.

---

### Post by blackened on 2009-09-24
Hmmm... SIS.  Never owned one, and have never tried to configure one, but we can give it a shot.

Please post the output of
```
xrandr --prop
```

---

### Post by g_lev on 2009-09-24
```

Screen 0: minimum 320 x 240, current 960 x 600, maximum 960 x 600
default connected 960x600+0+0 0mm x 0mm
   960x600        60.0* 
   960x540        60.0  
   800x600        60.0     56.0  
   768x576        60.0  
   720x576        60.0  
   856x480        60.0  
   800x480        60.0  
   720x480        61.0  
   640x480        60.0  
   400x300        60.0  
   320x240        61.0  

```

---

### Post by blackened on 2009-09-24
Ok.

Cut and paste the output from 
```
sudo ddcprobe
```

if ddcprobe isn't installed, then
```
sudo apt-get install xresprobe
```
and try again.

---

### Post by g_lev on 2009-09-24
```

vbe: VESA 3.0 detected.
oem: SiS
vendor: Silicon Integrated Systems Corp.
product: 6330 2.20.00
memory: 16384kb
mode: 800x600x16
mode: 640x480x256
mode: 640x400x256
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x256
mode: 320x200x32k
mode: 320x200x64k
mode: 640x480x32k
mode: 640x480x64k
mode: 800x600x32k
mode: 800x600x64k
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1280x1024x32k
mode: 1280x1024x64k
mode: 640x480x16m
mode: 800x600x16m
mode: 1024x768x16m
mode: 1280x1024x16m
edid: 
edidfail

```

---

### Post by blackened on 2009-09-24
That's what I figured. You wouldn't happen to have the monitor's manual laying around anywhere would you? Or happen to know the hsync and vrefresh ranges off the top of your head?

I wasn't able to find much information about this monitor on the web. If we had the ranges, then we could manually add them to xorg.conf and it should give you back the appropriate resolution choices.

---

### Post by g_lev on 2009-09-24
[http://reviews.cnet.com/crt-monitors/mag-innovision-996pf/4507-3175_7-20377797.html?tag=mncol;psum](http://reviews.cnet.com/crt-monitors/mag-innovision-996pf/4507-3175_7-20377797.html?tag=mncol;psum)

[http://www.tigerdirect.com/applications/searchTools/item-details.asp?sku=M925-1904](http://www.tigerdirect.com/applications/searchTools/item-details.asp?sku=M925-1904)

any good ?

---

### Post by blackened on 2009-09-24
That should work. I'm going to assume you've made no modifactions to xorg.conf already and that it's pretty bare when you open it. If that's the case, then you should just be able to cut and paste this stuff in. If you have made modifications to the file before, then we need to stop and make a backup.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Otherwise we can go straight to editing.

```
gksudo gedit /etc/X11/xorg.conf
```

Replace the monitor section, but leave everything else alone.

```
Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync          30-96
	VertRefresh        50-160
EndSection

```

---

### Post by g_lev on 2009-09-24
PERFECT !!!
Thank you very very very much ):P

---

