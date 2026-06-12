---
title: "Web Cam problems"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by Archie69 on 2009-09-12
Hey all,

I have an acer aspire laptop, and I run Ubuntu 8.04 and everything is great until today. I was trying to use skype and have a video conversation but the camera wasnt working. Could there be a problem with one of the updates ubuntu gives me? Could there be any other reason why it wouldnt work? 

It was working when I was home (last week) so I have no idea why it wouldnt be working now. Any help would be greatly appreciated.

Thanks

---

### Post by stderr on 2009-09-13
Hi Archie, what webcam do you have? This link [https://help.ubuntu.com/community/Webcam]("https://help.ubuntu.com/community/Webcam") may help somewhat. You can test your webcam's output through the installed driver this way, also articulated on that page: determine your webcam's device file (by unplugging your webcam, running 
```
ls /dev/video*
```
plugging your webcam in and running the same command again). 
Start VLC (if you haven't got VLC - a great free video player - run
```
sudo apt-get install vlc
```
), run it, File->Open Capture Device, enter the device name (discovered above - /dev/videoSOMETHING) and see what output you get, if any.

If you've got no discernable output, or an error message, post that back along with your webcam's details, and any steps you can recall you took to install drivers for it in the first instance, if any. It would also help to post the output of: 

```
lsusb
```
(If you like, you can remove the lines that don't pertain to your webcam).

---

### Post by Archie69 on 2009-09-13
Thanks but I have a built in web cam so I wouldn't know how to disconnect it. Like I was saying, the webcam was working with no problems at all a week ago.  Now I'm in a hotel using their wifi so I was hoping that is the problem and it will be fixed once i have my own place. Could that be it?

---

### Post by Archie69 on 2009-09-28
Isusb said this:

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 064e:a101 Suyin Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

also I ran Ispci and it shows this:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

Hopefully someone can help. As for what steps I had to take initially to get the web cam going...there were none. It worked perfectly till a few weeks ago, which I found odd. Doesn't work in Skype, msn, cheese, or anything else.  They all default to the web cam, but it doesn't work.

---

### Post by Archie69 on 2009-09-28
Anyone? Any advice or help would be great

---

### Post by Archie69 on 2009-09-29
Anyone?
Anything?

---

### Post by howefield on 2009-09-29
> **Archie69 said:**
> Anything?

Yes, try keeping the same issue in one thread.

Might be easier to buy a cheapo camera to get you up and running, eg Logitech E3500 less than a tenner. Let you get up and running whilst you get the issue with the built in camera sorted out.

---

### Post by Archie69 on 2009-09-29
Appreciate it, however I'd like to get the issue sorted sooner rather than later and avoid buying a camera. I would if I was receiving an error message or something, but the fact of the matter is, that the web cam was functioning perfectly, then up and quit. Strange I thought, and would like to fix it is all. Thanks

---

### Post by bwallum on 2009-09-29
stderr's advice is good using vlc to test your webcam. Have you tried that? What was the result?

---

### Post by Archie69 on 2009-09-29
I've tried using VLC to use my cam, but it doesn't show anything. There is no output at all. The indicator light on my web cam doesn't even turn on. I have however tried to use it on skype and cheese and the indicator light does turn on but no images are being show. I then took the next step suggested and ran lsusb and have pasted the output on here. I also ran lspci and have that posted as well. Any suggestions from here?

---

### Post by khelben1979 on 2009-09-29
In [Kopete]("http://en.wikipedia.org/wiki/Kopete") you have the possibility to change your video settings. I recommend you take a look at it and experiment a little to see if it helps.

B.t.w. the settings will affect Skype as well.

---

### Post by Archie69 on 2009-09-29
I'll give that a try. But in my mind, that should function similar to skype, amsn, cheese, and the many other web cam software that my web cam is not working with.

I have been searching online and it says that you may have to reinstall a driver, but i have no idea how i would reinstall a driver in ubuntu as i'm sure there is no linux based download option via acer.

Any other ideas are welcomed. Thanks a lot

---

### Post by Archie69 on 2009-10-09
Can someone re-read this and give me some advice? The web cam is still not working and would like to get it going.

---

### Post by khelben1979 on 2009-10-09
> **Archie69 said:**
> Can someone re-read this and give me some advice? The web cam is still not working and would like to get it going.

If the light of the web cam lights up when you start Skype, it should be working. Did you try the settings using Kopete?

Other than that, I would advice you to get a cheap webcam as suggested already. It's the easy way.

Sometimes new Ubuntu kernels mess up. Look for different versions of the Linux kernel in [Synaptic]("http://en.wikipedia.org/wiki/Synaptic_%28software%29") and install an older one. I think this is the source of your problem.

---

### Post by arrange on 2009-10-09
You probably don't have to install an older kernel, just boot into one when seeing the grub options after boot.

---

### Post by bwallum on 2009-10-09
Keep with the latest kernel would be my advice to. I get good webcam usage by ensuring that I have a 'driverless' can, i.e. not a cam built around M$.

This one works with Ubuntu, there may be others but I can recommend this one because I use it and it is a good little cam but I have not tried others:
[http://cgi.ebay.co.uk/8-0M-DRIVERLESS-WEBCAM-DIGITALZOOM-NIGHTVISION-SNAPSHOT_W0QQitemZ250502064914QQcmdZViewItemQQptZUK_CamerasPhoto_DigitalCameras_DigitalCameras_JN?hash=item3a53162b12&_trksid=p3286.c0.m14](http://cgi.ebay.co.uk/8-0M-DRIVERLESS-WEBCAM-DIGITALZOOM-NIGHTVISION-SNAPSHOT_W0QQitemZ250502064914QQcmdZViewItemQQptZUK_CamerasPhoto_DigitalCameras_DigitalCameras_JN?hash=item3a53162b12&_trksid=p3286.c0.m14)

---

