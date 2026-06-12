---
title: "Help with Belkin 7051 USB wireless"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by glendavee on 2006-11-21
I'm completely new to Ubuntu (and Linux). When I run 6.10 from a CD I can't connect to internet via wireless router. As this is my only connection option, this makes downloading drivers and stuff difficult. I have a Belkin 7051 usb wireless card which has a Broadcom chipset. I can see the device listed if I "sudo lsusb". Can I download a driver via windows onto CD and then instal it from the CD when running Ubuntu? If so can anyone suggest a suitable one?
Yours in confusion

---

### Post by FrodoB on 2006-11-21
Here is a link to the ndiswrapper site:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

Your device is listed and they got the drivers from the Windows CD:

Card: Belkin F5D7051 (USB 2.0 Adaptor 802.11g 125Mbps) [LIST]
[*]Chipset: BCM4320
[*]usbid: 050d:7051
[*]Driver: Used hidden driver's from installation CD - bcrndis.inf - installation via commandline - configuration via controlcenter.
[*]Other: Tested on Mandriva 2006 Free - ndiswrapper 1.13
[*]Other2: Keyboard freezes on hotpluging.[/LIST]

---

### Post by glendavee on 2006-11-22
Thanks, I'll give it a go and report back

---

### Post by glendavee on 2006-11-23
Sorry, but I'm obviously more intellectually challenged on ubuntu than I thought. I can't find the bcrndis.inf file, either on the ubuntu installation CD or the Belkin driver CD. How/where do I access the file??

---

### Post by Puzzled_Pete on 2006-11-23
Hi glendavee,

I'm in the same situation as you, but I have found the .inf file which by the way is "BCMRNDIS.inf" and is on the Belkin installation CDROM.  You can find it using Windows Explorer in Windows.

---

### Post by glendavee on 2006-11-23
Thanks Pete
I will have a look for it, transfer it to a usb memory stick and try it while running ubuntu from the cd.

---

### Post by glendavee on 2006-11-23
Pete, anybody
There is a bcmrdis file on the belkin cd, but it is a text file, not an .inf file
yours in confusion

---

### Post by FrodoB on 2006-11-23
The .inf files are textual, they explain the inner workings of the .sys file which is also required to the program that is communicating via the NDIS blob.

---

### Post by Puzzled_Pete on 2006-11-24
BCMRNDIS.inf is a hidden file and will only show up in Windows explorer if explorer is set (in Tools, Folder Options, 'View' tab) to show 'all hidden files and folders. Try that and see if it helps.  If not you have different installtion disc to the one I'm using.  Have Fun.  P-P

---

### Post by infol on 2007-01-05
i got my f5d7051 working by following this howto [HTML]http://www.ubuntuforums.org/showthread.php?t=225206[/HTML], obviously replacing wusb54g.inf (or whatever it was called) with bcmrndis.inf and exchanging the vendor/product id's in javajake's udev mod (as i run edgy) to match that of the f5d7051 - please note that 7051 is the product id and 050d is the vendor id.

hope this helps

---

### Post by glendavee on 2007-01-05
Infol - many thanks. What I did was abandon the Broadcom USB dongle, and switch to a new Belkin dongle (Belkin 9050 MIMO dongle which uses Airgo Networks chipset) . This worked fine with ndiswrapper 1.31

---

### Post by theDaveTheRave on 2007-03-06
Here is a link to JavaJake's howto in installing another usb key.

I have used it to install my belkin F5D7051 usb key, and with a bit of jiggery pockery I have managed to get it working.

I did send a post to the thread, allmost at the end now, and Javajake and I are working on a howto update to include this info.

The only thing I can say is that I am using Dapper not Edgie.

The update from my end may take a little while as I'm in the middle of trying to find a job and get a university assesment in!

I'm about to perform the same action on an old compaq presario 700 laptop, so check back on the other thread for an update regarding that procedure.

Good luck on getting the key working, once it does the oddest thing is the signal strength, when I log in via XP the signal strength is abysmal... and keep dropping out. but with Dapper the signal runs at over 75% most of the time.


here is the link to javajake's howto:

[http://www.ubuntuforums.org/showthread.php?t=225206&highlight=javajake](http://www.ubuntuforums.org/showthread.php?t=225206&highlight=javajake)


DaveM

---

