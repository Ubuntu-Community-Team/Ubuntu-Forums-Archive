---
title: "ATMEL AT76C505 USB can't associate with hidden AP"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by noabody on 2007-06-06
The short question:  Is there any available Linux driver that will allow me to connect to a hidden SSID with 128 bit WEP encryption enabled?


Some backgroud: 

The device is an IBlitzz BWU613 USB adapter which is really just a rebranded AIN AWU-2000B.

Some info from the Windows .inf:

; Copyright 2000 ATMEL.
; AT76C505 based FastVNET USB 11M Network Adapter
; Supported OS: Windows 98se/Me/2000/XP
; For devices With RF2958 radio

I'm using ubuntu feisty with latest kernel which includes these versions of Berlios atmel linux driver:
at76c503a-source (0.14~beta1-3)
atmel-firmware (1.3-2)

I'm connecting to a Linksys BEFW11S4 or WRTP54G - tried both.
I'm using 128 bit WEP with HEX key and SSID transmit is disabled (hidden ESSID).

So here's the deal, I can connect only if I enable SSID transmit.  If I hide my SSID I can't connect.  Some of the earlier Berlios readme files say that will be the case but it's unclear if the bug exists in any of the current versions of the driver.  In fact I was just curious if anyone knows for sure if connecting to a hidden SSID is or is not possible.  If anyone has gotten it to work then please post what driver/firmware version.

And when I say if it does/does not work, I mean for any USB AT76C505 RF2958.

Also used (iwconfig wlan0 essid mynet nick mynet channel 11 enc restricted key 11:11:11:11:11:11:11:1 ap 11:11:11:11:11) with the hopes that explicity defining the ssid, channel, and ap code would allow me to associate properly; it didn't.  The funny thing is that my AP actually shows up on the list when i use (iwlist scan).  So it's not like the wireless card doesn't see it, it simply can't associate.  Of course the ESSID is shown as "".

---

