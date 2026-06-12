---
title: "Airlink AWLH3026 &amp; Linksys WRT54G"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by jkman on 2006-09-24
For starters, I am still new to the linux world.  I am working on getting this computer connected wirelessly and it has been a little more difficult then I thought it would be.

I have searched through threads similar to the issue that I am having, but none of them have helped.  I ran ifconfig, iwconfig and iwlist scan to help diagnose what might be the problem.

> spencer@JKSERVER:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8520981 (8.1 MiB)  TX bytes:1013658 (989.9 KiB)
          Interrupt:3 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:19725 (19.2 KiB)  TX bytes:19725 (19.2 KiB)

spencer@JKSERVER:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:"JKNETWORK2"
          Mode:Managed  Frequency:2 MHz  Access Point: 00:16:B6:D4:7B:D7
          RTS thr:off   Fragment thr:off
          Link Quality=85/70  Signal level:-51 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

spencer@JKSERVER:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:16:B6:D4:7B:D7
                    Mode:Managed
                    ESSID:"JKNETWORK2"
                    Encryption key:on
                    Channel:2

sit0      Interface doesn't support scanning.



The strange thing is that the card seems to be working (I think), but it is not connecting to the router.  I have tried turning off all security settings on the router just to see if I could get it connected, but that still did not work.

I would appreciate any help that you can offer on getting this up and running.

---

### Post by LicensedLuncay on 2006-10-15
I am having the same problem with the same card, Still no ideas?

---

### Post by dlauer on 2006-10-20
Hi all,
I have the same card. Its an internal wireless card (PCI) for thoose that don't know. 

My Problem is when I do not de-activate the card before shutting down I get freezes when trying to boot the next time. Now I'm stuck rebuilding because ifconfig freezes too.....

Any thoughts?

Thanks
Dave

---

### Post by WatsonJX on 2006-10-28
Hello,

I have the same AWLH3026 PCI card which is said to be based on RT61 chipset. 

I am on Dapper with kernel 
Linux amd64 2.6.15-23-amd64-generic #1 SMP PREEMPT

modprobe rt51 (or rt2500) ieee80211-rtl
ra0 shows up in /proc/net/dev

However iwconfig ra0 essid My-AP just halt the command line.
iwlist scan also hangs.

Any idea how to get around it?

Thanks a lot.

---

### Post by WatsonJX on 2006-11-01
I got it working after a tiny fix.

rt61 cvs daily from rt2400.sf.net:

Fix this:

rtmp_info.c:
RTMPWPAAddKeyProc()

line 3525:
// 1. Check BSSID, if not current BSSID or Bcast, return NDIS_STATUS_FAILURE
if ((memcmp(pKey->BSSID, BROADCAST_ADDR, ETH_ALEN) != 0) &&
(memcmp(pKey->BSSID, pAd->PortCfg.Bssid, ETH_ALEN) == 0))
return(NDIS_STATUS_FAILURE);

The test for second memcmp() should be '!='. 

then WPAPSK works for me.

---

### Post by vergeh on 2007-09-25
> **WatsonJX said:**
> I got it working after a tiny fix.

rt61 cvs daily from rt2400.sf.net:

Fix this:

rtmp_info.c:
RTMPWPAAddKeyProc()

line 3525:
// 1. Check BSSID, if not current BSSID or Bcast, return NDIS_STATUS_FAILURE
if ((memcmp(pKey->BSSID, BROADCAST_ADDR, ETH_ALEN) != 0) &&
(memcmp(pKey->BSSID, pAd->PortCfg.Bssid, ETH_ALEN) == 0))
return(NDIS_STATUS_FAILURE);

The test for second memcmp() should be '!='. 

then WPAPSK works for me.

Umm...that fix sounds great...but how would I go about fixing this on my machine. Keep in mind I'm totally new to Linux.

---

