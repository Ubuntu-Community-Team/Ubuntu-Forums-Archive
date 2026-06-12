---
title: "Dlink Router and DWL-G650+"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by GaryS on 2006-10-01
Have set up dual-booting with XP, which is working ok.
Wireless works fine with XP but not with Ubuntu.

Below are details from ifconfig and iwconfig, any ideas.

-----------------------------------------------------------

wlan0     IEEE 802.11b+/g+  ESSID:"G604T_wireless"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=49/100  Signal level=29/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
==================================================

gary@(none):~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5136 (5.0 KiB)  TX bytes:5136 (5.0 KiB)

wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx (deleted by me)
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

---

### Post by dbarker on 2006-10-02
GaryS,

I too am a newbie ](*,) so I hope I can help. It took me a few days to get (K)ubuntu working with my wireless card (DWL-G520+). I found that when I installed 5.10 everything worked out of the box, but when I moved to 6.06 it stopped! I searched high and low and this is what I found:

1. The DWL-G520+/650+ uses the ACX chip set which by default is incorrectly configured on installation. The installation actually uses a version of drivers/firmware that does not work with this chipset! This bug has been logged not sure if it will be fixed in 6.10?

2. To fix this issue there are two ways - only one of which would work for me - and that is to copy an older set of the drivers/firmware to the default directory. The other way was to create a config file that told the system to use the drivers/firmware of a given version, but this didn't work for me.

I will try and dig up the documentation that I found on this. I had a lot more joy when I started looking for the chipset rather than the brand of network card.

Here is a list of cards & chipsets:
[URL="http://doc.gwos.org/index.php/D-LinkWireless"]
http://doc.gwos.org/index.php/D-LinkWireless[/URL]

Here is a good link on how to fix this issue (hopefully):

[URL="http://philbull.livejournal.com/13717.html"]
http://philbull.livejournal.com/13717.html[/URL]

Here are some more links that may be of assistance:

[URL="http://acx100.sourceforge.net/wiki/Firmware"]
http://acx100.sourceforge.net/wiki/Firmware[/URL]

[https://help.ubuntu.com/community/WifiDocs/Driver/acx111]("https://help.ubuntu.com/community/WifiDocs/Driver/acx111")

[https://help.ubuntu.com/community/WifiDocs/Driver/acx100]("https://help.ubuntu.com/community/WifiDocs/Driver/acx100")


If you still have problems let me know and I will check my system at home (currently at work). I am about to re-install 6.06 tonight so I will have to do this again...hopefully this is fixed in 6.10....

cheers and good luck :) 

d.

---

### Post by dbarker on 2006-10-02
Here is the bug report for those of you that are interested:

[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/30766]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/30766")

and 

[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/45162]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/45162")

And it looks like the first one is fixed!

---

### Post by GaryS on 2006-10-03
I have finally managed to get my D-Link DLW-G650+ to work with tee G604T router.
After adding the following:

options acx firmware_ver=1.2.1.34

to /etc/modprobe.d/options

---

