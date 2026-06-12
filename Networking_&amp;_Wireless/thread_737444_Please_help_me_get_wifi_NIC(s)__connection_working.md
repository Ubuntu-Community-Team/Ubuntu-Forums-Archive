---
title: "Please help me get wifi NIC(s) / connection working"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by anystupidname on 2008-03-27
Well, I'm really frustrated. I've been unable to get this Stinkpad's wireless connections to work in Linux Mint (ubuntu based) for a couple weeks now. Both the onboard 802.11b and the PCMCIA 802.11g can be used to connect to my linksys router in the (temporarily dual boot until I can get this working) Windows partition. If somebody could give me some pointers, I'd really appreciate it. I've tried too many different suggestions from these forums and others and I have quite a mess on my hands. I'm not sure where to go from here.

The router is setup for G or B WPA2 personal encryption.
The laptop has an onboard B NIC and a PCMCIA G NIC. (and an Intel wired NIC)

Currently, I have a ton of wireless utils installed of which I really only need one. Suggestions welcome for picking the best of the bunch. I'm sort of disappointed with all of them and not just because it isn't working :-/

What I've done so far:
-tried to resolve a possible problem with NIC detection/hardware enumeration
(a bogus wifi NIC was listed by the system)
-installed every wireless util I could find
-flashed new firmware onto intersil onboard wifi NIC
-blacklisted modules for onboard NIC in an attempt to simplify config of PCMCIA NIC
-purchased PCMCIA 802.11G NIC

Wireless stuff installed:
> wireless-tools/gutsy uptodate 29~pre20-1ubuntu1
kwifimanager/gutsy uptodate 4:3.5.8-0ubuntu2
madwifi-tools/gutsy uptodate 1:0.9.3+dfsg-1
wifi-radar/gutsy uptodate 1.9.7-0ubuntu4
mintwifi/unknown uptodate 1.7
kwlan/gutsy uptodate 0.6.2-1
linux-wlan-ng/gutsy uptodate 0.2.8+svn1832+dfsg-2ubuntu1
wlassistant/gutsy uptodate 0.5.7-2
prismstumbler/gutsy uptodate 0.7.3-0ubuntu2

iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:" "  Nickname:""
          Mode:Managed  Access Point: Not-Associated   Bit Rate:2 Mb/s
          Sensitivity=1/3
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

wlan0     IEEE 802.11b  ESSID:" "  Nickname:""
          Mode:Managed  Access Point: Not-Associated   Bit Rate:2 Mb/s
          Sensitivity=1/3
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wifi1     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig -a
> ath0      Link encap:Ethernet  HWaddr [MAC removed]
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr [MAC removed]
          inet addr:7.7.7.7  Bcast:3.3.3.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:67797212 (64.6 MB)  TX bytes:4399743 (4.1 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5185 (5.0 KB)  TX bytes:5185 (5.0 KB)

wifi0     Link encap:UNSPEC  HWaddr [MAC removed]-00-00-00-00-00-00-00-00-00-00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

wifi1     Link encap:UNSPEC  HWaddr [MAC removed]-00-00-00-00-00-00-00-00-00-00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

wlan0     Link encap:Ethernet  HWaddr [MAC removed]
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

Any assistance would be much appreciated!

---

### Post by anystupidname on 2008-04-07
I did a fresh install of hardy, blacklisted the hostap and hostap_pci modules, and got the PCMCIA NIC working via WPA2 using the instructions here:
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

Sadly, there still is a bogus wifi0 NIC with the same MAC as the correct NIC (ath0) followed by a bunch of 00:00:00:00....

---

