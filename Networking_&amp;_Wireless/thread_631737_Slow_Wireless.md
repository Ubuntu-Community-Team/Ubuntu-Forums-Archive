---
title: "Slow Wireless"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by dedtr9 on 2007-12-04
I did do a search for my problem, and couldn't get anything to work right, or couldn't decipher it.
My wireless network is very slow, I can ping my router with an average ping of 3 seconds and a 63% success rate. Here is my information from the different commands people ran in the other topics. I can't test wired because my computer is too far away from anything else.
```

01:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

*-network:1
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wmaster0
       version: 01
       serial: 00:12:17:8b:7d:1b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.101 latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11g


wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:06:DA:83   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     Link encap:Ethernet  HWaddr 00:12:17:8B:7D:1B  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe8b:7d1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95904534 (91.4 MB)  TX bytes:12470824 (11.8 MB)

```

---

### Post by lisati on 2007-12-04
Nothing glaringly obvious jumps out at me. I'm aware of a couple of things that can confound efforts to get wireless working at a level that people are comfortable with - stuff like making sure that there's nothing in between the various gadgets that can mask the signal (but no errors showing up in the report suggests that this might not be the issue).

The reported clock speed of 33MHz seems a little slow to me - perhaps someone who is more knowledgable on the techincal aspects of wireless gizmos might be able to confirm or correct this impression......

---

### Post by dedtr9 on 2007-12-04
It is steady at about 80% connectivity. There is nothing bad happening with the 64bit xp sitting next to it that is on the same network.

---

