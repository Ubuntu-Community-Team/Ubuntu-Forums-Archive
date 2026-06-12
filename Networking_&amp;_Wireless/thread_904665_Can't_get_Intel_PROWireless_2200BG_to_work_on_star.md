---
title: "Can't get Intel PRO/Wireless 2200BG to work on start-up"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by BandD on 2008-08-29
I'm working on a Vaio laptop.  The wireless card is an Intel PRO/Wireless 2200BG card.  Network manager doesn't recognize the wireless card after a boot/reboot.  I have to manually turn the wireless card off with the switch at the front of my computer, wait a few seconds, and then turn it back on again.  Then I'm able to select the wireless network of my choice and connect fine.

I've read several different threads about editing /etc/network/interfaces and/or /etc/rc.local but it's a little over my head.

Here is the output of lshw -C network:
```
*-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:06:04.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:09:c6:a9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.2.101 latency=32 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"RG-Beachouse"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:FD:7C:22   
          Bit Rate:48 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=82/100  Signal level=-48 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:5
```

and /etc/network/interfaces:
```
auto lo
iface lo inet loopback
```

I tried reading through man interfaces but I couldn't quite understand how to put everything together.  

Another thing to note is that the primary wireless network I use is WEP encrypted, though the WEP key is stored in the Keyring.  

Thanks for any help you can offer!

---

