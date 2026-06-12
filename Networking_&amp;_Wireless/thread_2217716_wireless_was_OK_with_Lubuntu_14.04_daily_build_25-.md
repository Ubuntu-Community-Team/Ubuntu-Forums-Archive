---
title: "wireless was OK with Lubuntu 14.04 daily build 25-MAR but now NOT OK with rel 17-APR"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by parker-hugh on 2014-04-18
hp pavillion dv2036ea this old laptop has a 802.11g wireless adapter built in. But I have new 802.11n wireless adapter (bought from ThePiHut) that I have used on this laptop which was successfully recognised when I installed Lubuntu Trusty Tahr daily build on 25-MAR-2014.

But I have now downloaded latest release Lubuntu 14.04 Trusty Tahr on 17-APR-2014 and when I install this version, it doesn't recognise the wireless adapter.

The wireless adapter is Ralink Tech Corp RT5370

when I run sudo lshw, I get the following results...

*-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:6
       logical name: wlan1
       serial: 00:0f:55:a8:2e:38
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.13.0-24-generic firmware=0.29 link=no multicast=yes wireless=IEEE 802.11bgn

Any idea why I can't get wireless running with the latest Trusty Tahr?  I don't know how to install the driver manually as I am new to Linux, but  have a disc with the driver on it, in a zip file. If there are any step-by-step instructions I could try to use the terminal to install it.

any help would be appreciated.

---

### Post by lisati on 2014-04-20
Duplicate of [http://ubuntuforums.org/showthread.php?t=2217760](http://ubuntuforums.org/showthread.php?t=2217760) closed.

---

