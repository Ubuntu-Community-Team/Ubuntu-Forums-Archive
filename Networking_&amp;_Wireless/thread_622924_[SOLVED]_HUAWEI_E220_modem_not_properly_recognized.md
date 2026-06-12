---
title: "[SOLVED] HUAWEI E220 modem not properly recognized"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by Darksouled on 2007-11-25
Hi!

I recently got myself a HUAWEI E220 HSDPA modem, and I know it should be natively supported in Gutsy. It seems to be recognized in Device Manager, and it does not mount as a CDROM/Storage Device, but I just can't get it to work properly.

When I insert the modem into the USB port I can see, using "lsusb", that it's added:

```
...
Bus 003 Device 008: ID 12d1:1003
...
```

Now then I use "modprobe usbserial vendor=0x12d1 product=0x1003", and it should now be properly "set up", right?

Well, using "ls -al /dev/ttyU*" is only giving me one ttyUSB when it should be three:

```
crw-rw---- 1 root dialout 188, 0 2007-11-25 15:44 /dev/ttyUSB0
```

Of course wvdial won't be able to connect me to the internet:

wvdial hsdpa

```
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial<*1>: Sending: ATQ0
WvDial<*1>: Re-Sending: ATZ
WvDial<Err>: Modem not responding.
```


The weirdest thing is that I were able to go online with it yesterday, and then "ls -al /dev/ttyU*" showed three ttyUSB-devices; 0, 1 and 2. But suddenly it stopped working.

I don't think that the wvdial.conf file has anything to do with this problem, so I'm not posting the file data. By the way wvdialconf is also giving me a "not-working"-message.


Has anyone got any idea what I'm doing wrong? I've been studying several dozen posts, but no one seems to tell what to do if I only get ONE ttyUSB by typing "ls -al /dev/ttyU*".

I know it probably doesn't matter (correct me if I'm wrong, and the wvdial MIGHT be the cause of this problem), but the provider is Netcom of Norway.

---

### Post by Darksouled on 2007-11-26
Eh, forgot to mention one thing. I don't know if it is of importance, but it's worth a try.

When the modem did work properly, the name of the modem were included in the list when I used "lsusb", like this:
```

Bus 004 Device 001: ID 0000:0000  
[COLOR="Red"]Bus 005 Device 003: ID 12d1:1003 HUAWEI Technologies CO, LTD[/COLOR]
Bus 005 Device 002: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 005 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 05a9:7670 OmniVision Technologies, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

And now, its only the address:

```
...
Bus 005 Device 003: ID 12d1:1003
...
```

What may be the problem? The modem is confirmed to work on windows computers as of today, so that's not an issue.

---

### Post by mizwete on 2007-11-26
I have a Huawei E220, it has functioned ONCE... since then, a month ago, it can't be recognized.

No matter if I plug it IN and OUT,
no matter if i launch mknod /dev/ttyUSB0 - then usb1 then usb2, the modem can't find the 3 nodes ( but ls -la /dev/ttyU*  shows the 3 nodes ).

dmesg gives errors messages, especially error 71, which I found is often related with faulty devices.

---

### Post by Darksouled on 2007-11-26
Well, it seems the tides have turned. A slight turn, but still.

I just tried to boot Ubuntu with the USB modem plugged in, and it actually worked. "ls -al /dev/ttyU*" indicated that three nodes were active/connected, as it should; /dev/ttyUSB0, /dev/ttyUSB1 and /dev/ttyUSB2. However, when I removed and inserted the modem again it didn't work (as expected). Only /dev/ttyUSB0 were shown and the modem were unable to initialize.


[COLOR="Red"]So I guess the question now is: What is wrong with the hotplugging, and how do I fix it? Is there any way to go through (parts of) the hardware-detection routine without having to reboot? [/COLOR]

I have used Ubuntu/linux less than a month, so anything dumbed down to next to nothing would be very nice.

---

### Post by craigtyson on 2007-11-27
If you do a dmesg you will probably see the E220 loaded as a SCSI device and thats the problem.  There is a patch for 6.06 I have applied it to my 7.10 laptop but it didn't work today. But I will post an update when I have tried it out on the road tomorrow.  If it works for me Il port the link otherwise not.

C

---

### Post by Darksouled on 2007-11-27
Thanks, that would be great!


**EDIT: **

[B]Problem solved! 
I managed to find a sweet driver package from the Swedish Vodafone. I installed it and everything seems to work perfect so far. However, as of now the only cards supported are Huawei E620, Huawei E220 and Option GlobeTrotter 3G+ EMEA. It has also only been tested to work flawlessly on Linux 2.6.17 kernels and later. But anyway, Google is my best friend right now. :D[/B]

---

### Post by YaseenKriel on 2007-12-01
using the same software for my usb modem. it can be downloaded here:

[http://www.tectonic.co.za/view.php?id=1596](http://www.tectonic.co.za/view.php?id=1596)

---

### Post by mizwete on 2007-12-01
I have found that a faulty usb cable was preventing the modem to be functionning properly.

Now it is solved.

---

### Post by Darksouled on 2007-12-01
> **YaseenKriel said:**
> using the same software for my usb modem. it can be downloaded here:

[http://www.tectonic.co.za/view.php?id=1596](http://www.tectonic.co.za/view.php?id=1596)

Oh yeah, I forgot the link it seems.

Direct link: [[COLOR="Red"]Vodafone Mobile Connect Card Driver[/COLOR]]("https://forge.vodafonebetavine.net/projects/vodafonemobilec/")

---

### Post by beemerbiker on 2007-12-13
Darksouled:

I have EXACTLY the same problem as you described in post #1 on this thread two weeks ago.  I gave up after a week of following promising leads, and had to pass the laptop back to my daughter, reverting back to Windows to get the Huawei E220 3G modem to work.  I'll get another brief crack at the laptop when my daughter comes home for one day at Christmas.  I'll try the boot up with the modem plugged in (although I thought I'd tried that before).  I'm not sure about the Vodafone driver that solved your problem.  Is your Huawei E220 modem a Vodafone-associated device?  The one I am working with was provided by the 3G mobile supplier '3' in the UK, so I don't know whether it's the same as a Vodafone device.  Any comments?

---

### Post by Darksouled on 2007-12-19
> **beemerbiker said:**
> Darksouled:

I have EXACTLY the same problem as you described in post #1 on this thread two weeks ago.  I gave up after a week of following promising leads, and had to pass the laptop back to my daughter, reverting back to Windows to get the Huawei E220 3G modem to work.  I'll get another brief crack at the laptop when my daughter comes home for one day at Christmas.  I'll try the boot up with the modem plugged in (although I thought I'd tried that before).  I'm not sure about the Vodafone driver that solved your problem.  Is your Huawei E220 modem a Vodafone-associated device?  The one I am working with was provided by the 3G mobile supplier '3' in the UK, so I don't know whether it's the same as a Vodafone device.  Any comments?

Hi!

I'm pretty sure the Vodafone drivers will work for you too. My supplier is the Norwegian Netcom, and it works just great. I think the Vodafone drivers just ensures that Ubuntu recognizes the HUAWEI for what it is, namely a cellular modem, and thus enabling them to communicate properly. If this is the case, then it WILL work for you too (assuming that you have no hardware issues).

Now my modem starts working flawlessly as soon as it is plugged in, and it's stable as h***. :) 


Good luck and merry Christmas to you. :)

EDIT: Just recalled that I read about a guy who made the Vodafone drivers work with '3' in Sweden, so I'm sure yours will work great too.

---

### Post by jpgeek on 2008-02-05
I have exactly the same problem on Ubuntu 7.10 with an E220 using EMobile in Japan.  

DO NOT USE THE VODAFONE DRIVER IF YOU ARE ON EMOBILE. You could have trouble with other non-european carriers as well.   It will stuff your card up and you wont be able to use it at all (even on Windows).

I have found that if I reboot twice with the card attached, it works.  If anyone finds a workaround for it I would love to hear it.

---

### Post by jpgeek on 2008-02-05
Solved again.

Short story:
[http://ph.ubuntuforums.com/showthread.php?p=3902243](http://ph.ubuntuforums.com/showthread.php?p=3902243)
(see mohdshakir post)

Long story
[http://www.mohdshakir.net/2007/12/05/huawei-e220-in-gutsy-gibbon-kubuntu](http://www.mohdshakir.net/2007/12/05/huawei-e220-in-gutsy-gibbon-kubuntu)

---

### Post by miamano on 2008-02-12
Hi,

I mean, this is a good workaround problem solving, but not the right way...

In my example:
Linux udesk3 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686 GNU/Linux

I turn my computer on, than...
Truncated from /var/log/kern.log:
Feb 12 07:09:48 udesk3 kernel: [   37.094575] usb 3-2: new full speed USB device using uhci_hcd and address 2
Feb 12 07:09:48 udesk3 kernel: [   37.257354] usb 3-2: configuration #1 chosen from 1 choice
Feb 12 07:09:48 udesk3 kernel: [   45.261198] usbcore: registered new interface driver usbserial
Feb 12 07:09:48 udesk3 kernel: [   45.261918] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial suppo
rt registered for generic
Feb 12 07:09:48 udesk3 kernel: [   45.262682] usbcore: registered new interface driver usbserial_generic
Feb 12 07:09:48 udesk3 kernel: [   45.262689] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Drive
r core
Feb 12 07:09:48 udesk3 kernel: [   45.270977] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial suppo
rt registered for GSM modem (1-port)
Feb 12 07:09:48 udesk3 kernel: [   45.271746] option 3-2:1.0: GSM modem (1-port) converter detected
Feb 12 07:09:48 udesk3 kernel: [   45.272859] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB0
Feb 12 07:09:48 udesk3 kernel: [   45.272886] usbcore: registered new interface driver option
Feb 12 07:09:48 udesk3 kernel: [   45.272890] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/option.c: USB Driver for GSM m
odems: v0.7.1

**Hoops, during the boot?!? Disconnect? Why?**

Feb 12 07:09:53 udesk3 kernel: [   55.384271] usb 3-2: USB disconnect, address 2
Feb 12 07:09:53 udesk3 kernel: [   55.384443] option 3-2:1.0: device disconnected
Feb 12 07:09:54 udesk3 kernel: [   56.404153] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Feb 12 07:10:03 udesk3 kernel: [   65.297637] usb 3-2: new full speed USB device using uhci_hcd and address 3
Feb 12 07:10:03 udesk3 kernel: [   65.460448] usb 3-2: configuration #1 chosen from 1 choice
Feb 12 07:10:03 udesk3 kernel: [   65.462432] option 3-2:1.0: GSM modem (1-port) converter detected
Feb 12 07:10:03 udesk3 kernel: [   65.462824] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB0

**Than restart:**
Feb 12 07:13:48 udesk3 kernel: [   45.399498] usbcore: registered new interface driver usbserial
Feb 12 07:13:48 udesk3 kernel: [   45.399549] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support
 registered for generic
Feb 12 07:13:48 udesk3 kernel: [   45.399619] usbcore: registered new interface driver usbserial_generic
Feb 12 07:13:48 udesk3 kernel: [   45.399623] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver 
core
Feb 12 07:13:48 udesk3 kernel: [   45.406531] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support
 registered for GSM modem (1-port)
Feb 12 07:13:48 udesk3 kernel: [   45.406593] option 3-2:1.0: GSM modem (1-port) converter detected
Feb 12 07:13:48 udesk3 kernel: [   45.407114] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB0
Feb 12 07:13:48 udesk3 kernel: [   45.407139] option 3-2:1.1: GSM modem (1-port) converter detected
Feb 12 07:13:48 udesk3 kernel: [   45.407620] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB1
Feb 12 07:13:48 udesk3 kernel: [   45.407645] option 3-2:1.2: GSM modem (1-port) converter detected
Feb 12 07:13:48 udesk3 kernel: [   45.408116] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB2
Feb 12 07:13:48 udesk3 kernel: [   45.408144] usbcore: registered new interface driver option
Feb 12 07:13:48 udesk3 kernel: [   45.408148] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1

Modem properly recognized.
It's not so funny...
Ok, I can modificate the modprobe -r uhci_hcd/modprobe uhci_hcd script for init. But...
Any idea why works modem after init 6 (and why disconnect at simple boot)?

---

### Post by DokuroSama on 2008-04-27
I live in Japan and I just put 8.04 on my Thinkpad r61

I use an Emobile D02HW 3g card.

After looking around for ways to make this work.  The simplest answer that worked was this:

Install PPP-Config
```
sudo apt-get install pppconfig
```

Make the profile file for it, so when you are done here do SAVE AS
```
sudo gedit /etc/ppp/peers/em-usb
```

Add this code to the file
```

user "em@em"
connect "/usr/sbin/chat -v -f /etc/chatscripts/pap -T *99***1#"
/dev/ttyUSB0
115200

noipdefault
usepeerdns
defaultroute
persist
noauth

```

Save As

Then enter this in the terminal

To turn it on:
```
pon em-usb
```

To turn it off:
```
poff em
```

I hope this helps!  I beat my head trying to get this work for like 5 hours.  Going through all the Japanese sites.  

If it doesn't work for firefox, make sure that you are working online!...not that I had that problem :roll:

Hope this gets you going.  The number for us here is *99***1#, so if you have a different number, put it there.

Regards
DS

---

### Post by DokuroSama on 2008-04-27
Sorry, the last part should be 
```

poff em-usb
```

---

