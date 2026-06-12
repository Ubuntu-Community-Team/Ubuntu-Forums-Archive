---
title: "zoneminder 0fps idle"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by narcoleptik.ninja on 2009-05-26
Hello all,
 
This is my first forum post and I have Googled for a solution to this problem but can't seem to turn up any relevent results. I am running jaunty ubuntu server and am trying to install zoneminder. 
 
I'm u[COLOR=black]sing a Philips[/COLOR] [SPC110NC]("http://www.amazon.com/Philips-Webcam-SPC110NC-27/dp/B001IWK4VE/ref=sr_1_7?ie=UTF8&s=electronics&qid=1243368909&sr=1-7") and it shows on the compatibility list. I hav[COLOR=black]e [/COLOR]gotten as far as able to access the zoneminder interface through my browser and can add a source but no luck for the video output. 
 
It only displays 0fps and a status of idle. For the source path I've tried both /dev/video and /dev/video0 (It's a little confusing on the interface since right under it there is a dropdown for video channel #). 
 
I'm guessing this isn't a problem with zoneminder, and most guides say to test the webcam with another program before running zoneminder, but I don't have a gui installed and this is the only web interfaced cam program I know... 
 
My dmesg results pertaining to the webcam...
 
```

[   12.763676] Linux video capture interface: v2.00
[   12.924816] uvcvideo: Found UVC 1.00 device Philips Webcam (0471:204a)
[   12.930650] iTCO_vendor_support: vendor-support=0
[   12.933429] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   12.933607] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   12.933711] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.045937] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.045994] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.101207] input: Philips Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.2/1-5.2:1.0/input/input4
[   13.112251] usbcore: registered new interface driver uvcvideo
[   13.112294] USB Video Class driver (v0.1.0)
[   43.267092] lp0: using parport0 (interrupt-driven).
[   43.565349] Adding 2441840k swap on /dev/sdb5.  Priority:-1 extents:1 across:2441840k
[   44.030971] EXT3 FS on sdb1, internal journal
 

```Any further help would be greatly appreciated
 
*edit: this thread may be better suited for multimedia & video...sorry
 
**edit: Added some extra lines from the dmesg output

---

### Post by narcoleptik.ninja on 2009-05-27
bump

---

### Post by narcoleptik.ninja on 2009-05-27
Any ideas? :(

---

### Post by noblow91 on 2010-11-28
I know this thread is over a year old and all, but I am having the same problem. I just found a list of tutorials for each distro of Ubuntu. I'm going to check it out now. 

[http://www.zoneminder.com/wiki/index.php/Ubuntu#Guides_for_Ubuntu_Desktop]("http://www.zoneminder.com/wiki/index.php/Ubuntu#Guides_for_Ubuntu_Desktop")

Sorry. The list is for installation of Zone Minder, not for getting the cameras to work.

---

### Post by no2498 on 2010-11-28
noblow91

you try the cam in cheese yet
look in sound and video for it
cheese webcam booth

lsusb should give you the make & model #

in case you need a driver

---

