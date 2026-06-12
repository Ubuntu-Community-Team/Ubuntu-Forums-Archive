---
title: "Cell phone no longer showing up as mass storage"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by dalum on 2009-05-02
I was running Ubuntu and Kubuntu 8.10.  K on a full desktop and Ubuntu on my eeePC.  I started with doing an IMG install on my eee 701 and was still able to use my LG Vu as external storage with a 4 gig card.  About 2 weeks before 9.04 came out of beta, I got a system update and my phone stopped working.  Went to my K/8.10 install and it still worked.  For some dumb reason, I agreed to try out/upgrade to the 9.04 beta on that machine.  My Vu stopped working.  My phone will change screens stating that it's running as mass storage but it never shows in the mountable drives list.  There seems to be nothing anywhere that shows in any searches showing what the error I get means using dmesg.

usb-storage: probe of 3-2:1.0 failed with error -5

The dmesg lines that I get when I plug un my phone are as follows:
> [ 7462.488105] usb 3-2: USB disconnect, address 17
[ 7556.720095] usb 3-2: new full speed USB device using uhci_hcd and address 18
[ 7556.916892] usb 3-2: configuration #1 chosen from 1 choice
[ 7556.960103] usb-storage: probe of 3-2:1.0 failed with error -5
What else do I need to probe/post to see if I can get this to work again?

Also, my phone mounts and software autoruns the softare I have installed on that 4 gig card.  Using an SDHC card adapter, the card is completely mountable and usable.  What sucks is that I did a full reinstall of the non-beta  of Ubuntu thinking that it was an issue of some odd beta code... nope.  Maybe it was a way I formatted my card?  Nope as well.  (used the HP USB formatting tool installed on my wlfe's Vista laptop)  This is making my personal productivity with my phone realllllly useless since it's taken a dump on me.  Everything else in 9.04 is awseome and amazing!

Any and all help is appreciated in advance!

---

### Post by dalum on 2009-05-03
I was hoping that there was going to be a better response than this.  I was thinking I'll just start from scratch again with Ubuntu 8.10.  Does anyone think I shouldn't because there's some magical fix for this?

---

### Post by SLEEPER_V on 2009-05-03
wow.  Sorry for the underwhelming response.  I dont have an answer for you.  I'm a noob, but I dont mind giving you a bump.

---

### Post by ravi_buz on 2009-05-03
Well i also had the same problem , Ubuntu8.04 and 9.04 are able to recognise the memory card as mass storage device but 8.10 fails to do so.

---

### Post by coffeeaddict22 on 2009-05-03
Hi,
You've possibly got a few options.  If you can connect with Activesync, multisync is now getting to a usable state.  there's a few important features in development, but it might be your answer.  

If you're looking to use it simply as a USB drive, a good start would be the output of ```
lsusb
``` which would give some idea as to whether it's recognised at all.

---

### Post by dalum on 2009-05-03
Well in a fit of stupidity, I went and downloaded v8.10 and fixed my problem by downgrading.  I'll post my lsusb info from my Kubuntu machine downstairs when I go down there to record my next podcast later this afternoon.

The good news is that my issues with my most used machine are cleared up by running 8.10.  I know it's hardly a good fix but I spend a good portion of my day with my eeePC 701 that it was almost a necessity to get it working with my phone.

for the record/comparison, my USB devices list:
> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 003 Device 003: ID 05c6:1000 Qualcomm, Inc.** 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 13fe:1f00 Kingston Technology Company Inc. DataTraveler 2.0 4GB Flash Drive
Bus 001 Device 004: ID eb1a:2761 eMPIA Technology, Inc. 
Bus 001 Device 003: ID 0cf2:6225 ENE Technology, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
The one in bold is my phone.

Also forgot, my phone isn't a PocketPC so ActiveSync isn't going to be a valid option for my issue.  (Unless I'm missing something?)

---

### Post by dalum on 2009-05-03
Hmmm, looks  like I spoke too soon about Active/Multisync... I just checked out the site for MultiSync.  This looks like this might remedy a different issue for my phone!  

Thanks for the off the wall fix for something else!  :D

---

### Post by scabootssca on 2009-05-06
Sorry for hijacking your thread.

I have the exact same problem, lg vu, 4gb micro sd card, used to work in ubuntu 8.10 doesn't after I upgraded to 9.04. It works in windows so the cord and phone are good.

dmesg after a restart and a fresh plug in
> 
[  672.653058] usb 2-8: new full speed USB device using ohci_hcd and address 9
[  672.869066] usb 2-8: configuration #1 chosen from 1 choice
[  672.910406] Initializing USB Mass Storage driver...
[  672.922107] usb-storage: probe of 2-8:1.0 failed with error -5
[  672.922167] usbcore: registered new interface driver usb-storage
[  672.922174] USB Mass Storage support registered.


dmesg after i unplug it and plug it back in a couple times
> 
[  758.239295] usb 2-8: USB disconnect, address 9
[  759.693043] usb 2-8: new full speed USB device using ohci_hcd and address 10
[  759.910603] usb 2-8: configuration #1 chosen from 1 choice
[  759.915357] cdc_acm 2-8:1.0: ttyACM0: USB ACM device
[  760.371347] usb 2-8: USB disconnect, address 10
[  762.820915] usb 2-8: new full speed USB device using ohci_hcd and address 11
[  763.034280] usb 2-8: configuration #1 chosen from 1 choice
[  763.037842] cdc_acm 2-8:1.0: ttyACM1: USB ACM device
[  765.560315] usb 2-8: USB disconnect, address 11
[  768.233058] usb 2-8: new full speed USB device using ohci_hcd and address 12
[  768.446205] usb 2-8: configuration #1 chosen from 1 choice
[  768.480106] usb-storage: probe of 2-8:1.0 failed with error -5


Here is lsusb
> 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 009: ID 05c6:1000 Qualcomm, Inc. 
Bus 002 Device 006: ID 0443:002e Gateway, Inc. Millennium Keyboard
Bus 002 Device 005: ID 0443:002f Gateway, Inc. 
Bus 002 Device 004: ID 2001:3700 D-Link Corp. [hex] DWL-122 802.11b
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 002: ID 0545:8080 Xirlink, Inc. IBM C-It WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



When I plug it in as data mode New Mobile Broadband Connection appears but I am unable to connect with bitpim like I used to be able to.

dmesg
> 
[  528.148265] usb 2-8: new full speed USB device using ohci_hcd and address 8
[  528.363261] usb 2-8: configuration #1 chosen from 1 choice
[  528.366228] cdc_acm 2-8:1.0: ttyACM0: USB ACM device



lsusb
> 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 007: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone
Bus 002 Device 006: ID 0443:002e Gateway, Inc. Millennium Keyboard
Bus 002 Device 005: ID 0443:002f Gateway, Inc. 
Bus 002 Device 004: ID 2001:3700 D-Link Corp. [hex] DWL-122 802.11b
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 002: ID 0545:8080 Xirlink, Inc. IBM C-It WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by cKGunslinger on 2009-05-06
Oops - I posted a thread on this in Hardware Support before I found this thread.  

Very similar issue - LG VU (CU920) in Mass Storage mode (2GB MicroSD card) is not detected by Ubuntu (Jaunty - 9.04)  Works just fine in Vista.  Just got the phone, so no idea if it works in 8.10.

No luck with BitPim, either.  The USB isn't seen, unless I switch to "Data Sync" mode, then the USB port is seen, but still not usable.

---

### Post by llamabr on 2009-05-07
Try:

```
sudo rmmod ehci_hcd
```
or
```
sudo rmmod uhci_hcd
```

The first one should be correct, but you get a weird message.  I think it's the same module, though.

---

### Post by scabootssca on 2009-05-09
No luck

scabootssca@GREEN:~$ sudo rmmod ehci_hcd
ERROR: Module ehci_hcd does not exist in /proc/modules
scabootssca@GREEN:~$ sudo rmmod uhci_hcd
ERROR: Module uhci_hcd does not exist in /proc/modules

Any more ideas? Help would be greatly appreciated :)

---

### Post by gnssw on 2009-05-29
The same problem here. I've come from debian, where my LG KU250 worked very well.
I really do not understand why this happens with Jaunty, do I need to compile my own kernel?

dmesg is the same as the others, lsusb:

Bus 003 Device 012: ID 05c6:1000 Qualcomm, Inc.

---

### Post by PhrankDaChickenGeek on 2009-06-14
Same problem here. Worked connecting my LG CU515 as mass storage in 8.10, but doesn't work in 9.04



lsusb:

Set as Mass Storage:
```

Bus 003 Device 008: ID 05c6:1000 Qualcomm, Inc. 

```

---

### Post by Ramdidan on 2009-07-23
My LG HB620T had the same problem: The usb-storage module failed with error -5. After reading  [http://kerneltrap.org/mailarchive/linux-usb/2009/5/21/5776813/thread](http://kerneltrap.org/mailarchive/linux-usb/2009/5/21/5776813/thread)  about the problems with the usb id 05c6:1000, i tried adding the line```
 usb-storage option_zero_cd=2
```   to /etc/modules and it worked fine. Drawback of this workaround: modems with a emulated windows driver cd probably won't work.

---

### Post by gnssw on 2009-07-26
Thank you, that helped!

> **Ramdidan said:**
> My LG HB620T had the same problem: The usb-storage module failed with error -5. After reading  [http://kerneltrap.org/mailarchive/linux-usb/2009/5/21/5776813/thread](http://kerneltrap.org/mailarchive/linux-usb/2009/5/21/5776813/thread)  about the problems with the usb id 05c6:1000, i tried adding the line```
 usb-storage option_zero_cd=2
```   to /etc/modules and it worked fine. Drawback of this workaround: modems with a emulated windows driver cd probably won't work.

---

### Post by alphalux on 2009-08-24
Adding the line in "/etc/modules" also fixed my problem. I am using the Samsung Flipshot SCH-U900, copying data to/from a flash memory card. I might add, that I had the same problem when using another Linux distribution, upon upgrading from kernel 2.6.23.x to 2.6.30.3.

Thank you for the tip and the link.

---

### Post by tjwilli on 2009-11-30
I tried adding this line to /etc/modulues, but it didn't work for me. I an LG VU that used to work with 8.04, but not anymore with 9.04.

I found that if I removed usb-storage and added it in after boot, it worked, so I put these in /etc/rc.local:

```
modprobe -r usb-storage
modprobe usb-storage option_zero_cd=2
```

Is this the right place for this?

---

### Post by Pariah73 on 2009-12-26
Thank you very much, this worked for me also..another entry for the old Linux Notebook!
> **Ramdidan said:**
> My LG HB620T had the same problem: The usb-storage module failed with error -5. After reading  [http://kerneltrap.org/mailarchive/linux-usb/2009/5/21/5776813/thread](http://kerneltrap.org/mailarchive/linux-usb/2009/5/21/5776813/thread)  about the problems with the usb id 05c6:1000, i tried adding the line```
 usb-storage option_zero_cd=2
```   to /etc/modules and it worked fine. Drawback of this workaround: modems with a emulated windows driver cd probably won't work.

---

