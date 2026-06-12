---
title: "Internet on wire but not on wireless"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by emcus on 2008-01-25
Installed Ubuntu 7.10 a while ago and have been struggling with the wireless connection since. I finally got a working wireless connection, I think. The network monitor tells me it is sending and receiving packages anyway. But I can't access the router or the Internet. It works fine with wired connection to the router. 
I have added the wireless card's mac address to the mac filter list on the router, set up a new 128 bit WEP encryption and manually configured ubuntu with the SSID, WEP key and DHCP setting. I get an IP number but I can't ping the router or anything on the Internet. Any ideas what is wrong? It's a Netgear router (11mbps) and a Netgear WG311v2 (54mbps) wireless card. Haven't had any problems on Windows with it.

---

### Post by Hightide on 2008-01-25
Hi emcus

have you had a look at Kevdog's tutorial?

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

or gilfs thread

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

you may find them useful

:)

---

### Post by emcus on 2008-01-27
Thanks, I tried the Kevdog tutorial but I got this:

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any ideas?

---

### Post by emcus on 2008-01-30
Still no progress. I have tried:
No encryption - this makes it appear as if I was connected but I don't get an IP and can't ping anything
64 and 128 bit WEP encryption - I get to specify the password and then it waits for a while and the question returns
MAC filter on/off - no difference
Connecting to a different router - same results

So the next step would be to switch the wireless card, but it appears to be close to something that works so I don't want to give up just now :-)
Does anyone have any ideas of what I should try next?

---

### Post by ugm6hr on 2008-01-30
Just to help with a bit of info - it looks like you have an ACX111 chipset wifi card.

Judging from other posts here - the Gutsy driver for ACX chipsets is flaky.  Ndiswrapper seems to work...

Search for the card on here: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)

---

### Post by emcus on 2008-02-02
I switched to the Ndiswrapper with the WG311v2 driver but it didn't help. I still get "no dhcpoffers". But it tells me I'm connected to the wireless network when I hover the network icon so it's a bit strange. Thanks anyway!

---

### Post by kevdog on 2008-02-02
Can you post 

iwlist scan
ifconfig
lshw -C network

Just want to confirm some settings for you!

---

### Post by emcus on 2008-02-03
marcus@marcus-ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:19:3C:C8
                    ESSID:"default"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:18:4D:81:BF:60
                    ESSID:"ladda"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:14:78:63:10:F6
                    ESSID:"sjodin"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:15:E9:E2:47:C5
                    ESSID:"JAS "
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:13:46:BD:1A:AC
                    ESSID:"HMW"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:09:5B:D5:6A:30
                    ESSID:"ML"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-26 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 07 - Address: 00:19:5B:B9:0B:77
                    ESSID:"dlink"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

(It's the ML one I want to connect to,)

marcus@marcus-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:9F:31:FD  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe9f:31fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:2300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2240883 (2.1 MB)  TX bytes:296347 (289.4 KB)
          Interrupt:5 Base address:0x9800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:09:5B:8F:95:D8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:d3800000-d3802000 



marcus@marcus-ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:0c:6e:9f:31:fd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.0.4 latency=32 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: wlan0
       version: 00
       serial: 00:09:5b:8f:95:d8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg311v2 driverversion=1.51+NETGEAR, Inc.,06/17/2004,6. latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


Thanks for your interest. (It's the same problem I have posted about in the Ndiswrapper thread,)

---

### Post by kevdog on 2008-02-05
Cell 06 - Address: 00:09:5B:D5:6A:30
ESSID:"ML"
Protocol:IEEE 802.11b
Mode:Managed
Frequency:2.462 GHz (Channel 11)
Quality:100/100 Signal level:-26 dBm Noise level:-96 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Extra:bcn_int=100
Extra:atim=0

So what kind of encryption are you using?

---

### Post by emcus on 2008-02-05
WEP 128 bit and MAC filtering. (I tried connecting to an unprotected router with the same result.)

---

