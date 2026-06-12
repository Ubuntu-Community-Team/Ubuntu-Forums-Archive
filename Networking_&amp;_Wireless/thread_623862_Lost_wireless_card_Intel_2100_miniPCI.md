---
title: "Lost wireless card Intel 2100 miniPCI"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by broggyr on 2007-11-26
I was using this wireless connection flawlessly on a stock Dell Inspiron 500m since installation of Xubuntu about 3 weeks ago.  I brought it to work one day, and while troubleshooting a wired connection, I think I accidentally removed the required wireless driver.

lspci -v:
01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corporation Unknown device 2565
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at fcfff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

ifconfig:
eth1      Link encap:Ethernet  HWaddr 00:0D:56:DE:06:44  
          inet addr:172.21.121.133  Bcast:172.21.121.255  Mask:255.255.254.0
          inet6 addr: fe80::20d:56ff:fede:644/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3617823 (3.4 MB)  TX bytes:324974 (317.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5276 (5.1 KB)  TX bytes:5276 (5.1 KB)

(eth0 [wireless] is no longer listed)

iwconfig:
lo        no wireless extensions.

eth1      no wireless extensions.


I have the driver files needed for ndiswrapper, but I don't believe that is necessary (i think it was working before ndiswrapper).

What can I do to have the system re-detect this card or do whatever it needs to do to reuse this once-working card?  I have since uninstalled ndiswrapper (and can still connect via a wired connection, as the machine I am posting this from is the one in question).

Thanks, Broggyr

---

### Post by broggyr on 2007-11-26
After reading around, I tried 

modprobe ipw2100

and the card was now polling wifi networks.

---

### Post by broggyr on 2007-11-28
After all was said & done, the card appears to be looking for networks, but doesn't actually connect.  How can I make Xubuntu redetect this card as it did during installation?  I am not aware of hardware utilities...

---

