---
title: "Connection in Windows, Disconnects in Ubuntu"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by jba6511 on 2007-07-01
Everything worked fine until yesterday. As far as I can recall, the only changes made have been an update to automatix and I upgraded my router's firmware (WRT54G V6) to the latest firmware release. I am able to connect just fine with a 91% signal strength in windows, but I get 18% in Ubuntu. The connection also drops after a few seconds in Ubuntu only and tries to reconnect, and then asks me for the paraphrase password to connect (never did this before either). I tried changing wireless channels, with no results. I downgraded the firmware back to the previous firmware release as well, with no results. I am using an IBM thinkpad T60. Any ideas what is happening?

results of dig and ifconfig



blake@Lenovo:~$ dig [www.google.com](www.google.com)

; <<>> DiG 9.3.4 <<>> [www.google.com](www.google.com)
;; global options:  printcmd
;; connection timed out; no servers could be reached
blake@Lenovo:~$ 

blake@Lenovo:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:CF:09:97:22  
          inet6 addr: fe80::216:cfff:fe09:9722/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39070 (38.1 KiB)  TX bytes:50665 (49.4 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9393 (9.1 KiB)  TX bytes:9393 (9.1 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-09-97-22-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5047 errors:0 dropped:0 overruns:0 frame:23538
          TX packets:1096 errors:30 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:496089 (484.4 KiB)  TX bytes:95203 (92.9 KiB)
          Interrupt:21

---

### Post by kevdog on 2007-07-01
Are you sure you are still trying to connect to your router or someone else's.  

What is the result of:
iwlist scan

How did you install drivers for your card??
lshw -C network

---

### Post by jba6511 on 2007-07-01
I did not have to install any drivers for the card, worked right away. I am positive I am connecting to my router as I use a unique name.

---

### Post by jba6511 on 2007-07-01
Ran this while I was connected:  I connect to "office" network.

[PHP]blake@Lenovo:~$ iwlist scan
lo        Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:18:39:3F:06:16
                    ESSID:"office"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/94  Signal level=-51 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:18:F8:47:92:E8
                    ESSID:"Murphy"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/94  Signal level=-78 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:18:39:B3:E5:E8
                    ESSID:"BadAndy"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/94  Signal level=-78 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK  
          Cell 04 - Address: 00:0D:3A:2A:A2:E2
                    ESSID:"MSHOME"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/94  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:18:F3:E6:7E:4D
                    ESSID:"Rogers"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=15/94  Signal level=-80 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 06 - Address: 00:12:0E:50:6D:FD
                    ESSID:"EJand Evie"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/94  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 07 - Address: 00:18:39:46:E0:FE
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/94  Signal level=-78 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 08 - Address: 00:90:4C:7E:00:6E
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/94  Signal level=-59 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 09 - Address: 00:14:6C:DA:08:42
                    ESSID:"Stroud"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/94  Signal level=-77 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f0101000eff7f

irda0     Interface doesn't support scanning.

blake@Lenovo:~$ 
blake@Lenovo:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: iomemory:ee000000-ee01ffff ioport:2000-201f irq:20
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@03:00.0
       logical name: wifi0
       version: 01
       serial: 00:16:cf:09:97:22
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:edf00000-edf0ffff irq:21
blake@Lenovo:~$ [/PHP]

---

### Post by gerkin on 2007-07-16
Hi, check out my post here it might help:

 [http://ubuntuforums.org/showthread.php?p=3030748#post3030748](http://ubuntuforums.org/showthread.php?p=3030748#post3030748)

---

