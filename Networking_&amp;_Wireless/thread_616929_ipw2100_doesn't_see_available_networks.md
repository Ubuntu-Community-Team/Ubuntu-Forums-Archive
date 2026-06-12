---
title: "ipw2100 doesn't see available networks"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by ryanferreri on 2007-11-18
Hi All,

I have a ipw2100 card in my Dell laptop and although it seems to be running, it cannot scan to see available wireless networks, even when I'm sitting right next to the AP. I looked around at the other threads on this card and couldn't find anything that helped.

Thanks,
Ryan

**ifconfig eth3**

eth3      Link encap:Ethernet  HWaddr 00:0C:F1:2D:83:B3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:faffd000-faffdfff 

**iwconfig eth3**

eth3      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[B]
lshw -C network[/B]

  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth3
       version: 04
       serial: 00:0c:f1:2d:83:b3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
[B]
iwlist eth3 scanning[/B]

eth3      No scan results

---

### Post by ryanferreri on 2007-11-19
Uh, nevermind. Radio was disabled in BIOS. Enabled and all is working fine.

---

### Post by kevdog on 2007-11-19
Glad you got it working -- weird some line in the lshw -C network statement didnt show even a hint of a problem.

---

