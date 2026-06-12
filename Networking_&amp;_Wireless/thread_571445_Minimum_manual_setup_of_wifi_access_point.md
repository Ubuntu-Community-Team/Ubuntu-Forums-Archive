---
title: "Minimum manual setup of wifi access point"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by smuglr on 2007-10-09
Hi there, thanks for the help, despite going through several howto's I still seem to be unable to get a simple connection. I have setup the access point as shown below, with no password protection. I have also setup DHCPD on the AP machine.

Using KWifimanager, I can see the available network, however I am unable to conncet using either DHCP or manual IP settings.

I have also manually set the freq, channel accesspoint, and IP settings using ifconfig and iwconfig, but still I cannot ping the AP host.

I am hoping to find out what is the absolute minimum I require to connect to the host (without any security DHCP or ip forwarding?). After this point I can happily work through the rest myself ;).

I am using the zd1211b driver to run the dongle in the access point.

Regards and thanks,
Dougie


eth2      802.11b/g NIC  ESSID:"AAA"
          Mode:Master  Frequency=2.437 GHz  Access Point: 00:17:3F:90:17:18
          Bit Rate:1 Mb/s
          Retry: on   RTS thr=2432 B   Fragment thr: off
          Encryption key: off
          Power Management: off
          Link Quality=68/100  Signal level=32/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:257
          Tx excessive retries:728763  Invalid misc:0   Missed beacon:0

eth2      Link encap:Ethernet  HWaddr 00:17:3F:90:17:18
          inet addr:10.1.1.1  Bcast:10.255.255.255  Mask:255.0.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:259 dropped:0 overruns:0 frame:259
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1057 (1.0 KiB)

---

### Post by kevdog on 2007-10-09
Try taking a look at this post:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Maybe it will address your issue -- maybe not!

---

### Post by smuglr on 2007-10-10
That is more helpful, but unfortunately I still can seem to connect. The access point doesn't even register a DHCP request. I'm going to assume therefore that it is a problem with the driver (the zd1211b driver claims it supports master mode, though the driver has no community support).

If anyone can suggest any models of usb wifi dongles known to work in master mode under linux it would be much appreciated, I'm off to search for some now.

REgards,
and thanks for your help
Dougie

---

### Post by kevdog on 2007-10-10
How did you install the driver??

A lot of drivers that claim to be unsupported means that they dont run natively on linux.  Unfortunately this is mostly the rule and not the exception.  Have you tried ndiswrapper??

---

### Post by smuglr on 2007-10-10
I found three drivers for the usb dongle (some Belkin model).

The version which comes with Ubuntu and Debian is the zd1211rw and doesn't support master mode yet.

There is also a vendor based driver which is rather old, and a community based fork of the vendor based driver. This community-based one claims on the [website]("http://zd1211.wiki.sourceforge.net/VendorBasedDriver") that master mode is supported, but they will not offer support on this driver as they are currently working to update the new 'rw' driver. 

Fair play, I reckon for my needs it's better to invest in a card anyway. Thanks for all your quick responses. If I get any further I'll be sure to post here.

Cheers,
Dougie

---

### Post by kevdog on 2007-10-10
Just a question and learning point for me -- Why do you need master mode?? Isnt master mode for setting your wireless device to act like an access point?

---

### Post by smuglr on 2007-10-10
Yup, that's correct. I need an access point, and hoped to use the dongle which was lying around.

Cheers,
Dougie

---

