---
title: "How to configure Wireless Internet?"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by biancarei on 2008-11-26
Hi!

I just installed Ubuntu 8.04 LTS Hardy Heron on my Acer Aspire 4710. Everything seems working fine except the WLAN. i'm using Intel PRO/Wireless 3945ABG with iwl3945 as its driver. However, I can't scan, and when i tried to configure using the network admin it says, "The interface does not exist. Check that it is correctly typed and that it is correctly supported by your system." I don't have any problem connecting when i'm "wired". I'm really confused, how do i configure my wireless internet access? can anybody help me? =) 

Additional data below:

root@AcerAspire4710:~# lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:5d:a2:24
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.23 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:83:c0:4f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
------------------------------------------------------------
root@AcerAspire4710:~# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1b:77:83:c0:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
------------------------------------------------------------
root@AcerAspire4710:~# iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
-------------------------------------------------------------
root@AcerAspire4710:~# iwlist wlan0 scan
wlan0     Failed to read scan data : Resource temporarily unavailable
-------------------------------------------------------------
root@AcerAspire4710:~# ifup wlan0
Ignoring unknown interface wlan0=wlan0.
-------------------------------------------------------------

---

