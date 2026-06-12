---
title: "Yet another wireless issue"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by MdaG on 2006-11-19
I'm on my DELL D800 laptop and I'm having trouble getting my wireless connection to work. My wlan-card is a "Truemobile 1300 WLAN" and works fine in Win XP (dualboots). I've installed the Windows driver through ndiswrapper and setup the ESSID and HEX-key (WEP) through the ndiswrapper GUI. Unfortunately I still can's scan and find any accesspoints. I've tried scanning with "iwlist eth1 scanning", but no success. What do I do now?

I've made it work under Gentoo so I'd be surprised if it doesn't work with Ubuntu. I'm running Dapper.

*edit*
Some info from the shell... 

> :~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)
> :~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0D:56:3C:71:35
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11
> :~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:90:4B:1E:CA:30
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xc000
> :~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.
> :~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"pr0NsoFt"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions
> :~$ sudo iwgetid eth1
eth1      ESSID:"xxxxxxxx"

---

### Post by FrodoB on 2006-11-19
This thread looks like it covers your device quite well:

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=BCM4306](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=BCM4306)

---

### Post by trubblemaker on 2006-11-19
you've probably got a native driver/ndiswrapper issue.  edgy comes with native driver which will fight with you if you install ndiswrapper ontop of it.  check out some of the howto's in my signature for help

---

