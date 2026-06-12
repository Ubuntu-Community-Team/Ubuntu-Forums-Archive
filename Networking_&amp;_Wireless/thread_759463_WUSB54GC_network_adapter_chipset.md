---
title: "WUSB54GC network adapter chipset"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by sofasurfer on 2008-04-19
Trying to install a WUSB54GC wireless adapter. The manufacturer is Cisco. Manufactured 3/2007.
I found tons of info but it seems that before I can start I need to find out what chipset is used.

lsusb -v | less doesn't say anything about a chipset.
dmesg does not say anything about a chipset...that I can see.
It did say in one spot, "usbcore: registered new interface driver rt73usb"

Is this information helpful to find the chipset?

---

### Post by scottro on 2008-04-19
That one should sort of work out of the box.   By "sort of" I mean that it should be recognized as wlan0 or wlan1 at boot. 

To my shame, after having great success with it on Fedora, I recommended it to someone on these forums, who found that for them, it constantly lost connection.  Some more searching of these forums indicates that it doesn't seem to work that well, in general with Ubuntu.  

However, it should be seen when you boot--are you sure that it isn't?  (You can try something like iwlist and see there's anything indicating that it's at least seeing wireless networks.)

---

### Post by sofasurfer on 2008-04-19
iwlist shows nothing.
iwscan shows:
lo       Interface doesn't support scanning

eth0        "            "             "            "

wlan0 scan completed

cell 01 - address: 00:17:3F:1F:1A:2c

essid:   "Belkin54g" (This is my router)

channel: 1

Freq: 2.412 GHz

So I guess this shows that my network is detected.
When I go to System>Administration>Network I see no information. So I think I might need to configure the stuff seen here. Correct? Or no?

---

### Post by sofasurfer on 2008-04-20
iwconfig shows: wlan0 issid "Belkin54g". So I guess it is seeing my router.

When I pinged my router (ping -c 4 192.168.2.1) I got "4 packets transmitted, 0 received".

From here I'm lost. Anyone willing to help?

---

### Post by sofasurfer on 2008-04-20
lshw -C network shows:
description: wireless interface
physical id: 1
logical name wlan0
serial: 00:1a:70:36:c3:ea
capabilities: ethernet physical wireless
configuration: broadcast type=yes  multicast=yes  wireless=IEEE 802.11g

---

### Post by sofasurfer on 2008-04-21
'sudo iwlist wlan0 scanning' shows:

wlano    scan ompleted
cell 01-address 00:17:3f:f1:1a:2c
essid: belkin54g
channel: 1
frequency: 2.412 ghz
signal level: 58 dbm
encryption key: off
bit rates: 1 mb/s, 2 mb/s.....12 mb/s, 48 mb/s


'sudo iwconfig wlam0' shows:

wlan0 IEEE 802.11g
mode: managed
access point: not-associated
link quality:0   signal level:0   noise level:0

---

### Post by dlinuxor on 2008-04-23
Hello 

Information about your chipset/driver can be found here:

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

I strongly recommend you to use this driver instead:

[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

You can use "Monitor mode" with the last one ;).

---

### Post by sofasurfer on 2008-04-23
I am not having a problem at the moment.
I found some tutorials that I was sure would finally solve my problem, but before I tried them out I decided to try Hardy Heron.
I installed it and WALA!! the WUSB54GC connected. Of coarse I had to configure a couple settings first. But there is one little issue I am having with it.
If you want to read about it go to: [http://ubuntuforums.org/showthread.php?t=762901](http://ubuntuforums.org/showthread.php?t=762901)

I may still try the serial monkey driver a little later if I can not get my present problem (as mentioned in the above post) solved.

---

### Post by sofasurfer on 2008-04-23
This thread finished.
Problem eliminated for now through other means.
-------------------------------------------------

---

