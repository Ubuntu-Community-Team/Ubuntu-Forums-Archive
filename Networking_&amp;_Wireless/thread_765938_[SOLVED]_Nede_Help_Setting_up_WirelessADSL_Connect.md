---
title: "[SOLVED] Nede Help Setting up Wireless/ADSL Connection"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by ilych on 2008-04-24
Hello,

I am using Ubuntu 8.04 and having trouble connecting to the Internet. I connect wirelessly to a router which is connected to the Internet.

The last line of 'lspci' on my Dell Latitude D820 is:
```
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) 
```

[LIST=1]
[*]Am I correct that according to [_[COLOR="Blue"]WifiDocs/Driver/bcm43xx/Hardy[/COLOR]_]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy") I do not need to install a firmware code as in [_[COLOR="Blue"]Gutsy[/COLOR]_]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy")?
[*]In Gutsy, the network manager would pick up a wireless connection called "GW-AP11X", but in Hardy, it doesn't pick up any connections. Also, "sudo pppoeconf" returns "Sorry, I scanned two interfaces, but the Access Concentrator of your provider did not respond".
[*][Please see this _[COLOR="Blue"]thread[/COLOR]_ on how I connect to the Internet in Gutsy.]("http://ubuntuforums.org/showthread.php?t=759815")
[*]Following are some information that may be helpful in solving my problem:
```
[COLOR="Red"][SIZE="3"]**$ ifconfig -a**[/SIZE][/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:15:c5:24:58:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1626 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1626 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:81300 (79.3 KB)  TX bytes:81300 (79.3 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:17:31:a3:d8:3c  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wmaster0  Link encap:UNSPEC  HWaddr 00-17-31-A3-D8-3C-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

```

```
[COLOR="Red"][SIZE="3"]**$ iwconfig **[/SIZE][/COLOR]
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

```

```
[COLOR="Red"][SIZE="3"]**$ sudo lshw -C network **[/SIZE][/COLOR]
  *-network                
       description: Network controller 
       product: BCM94311MCG wlan mini-PCI 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 module=ssb 
  *-network DISABLED 
       description: Ethernet interface 
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:15:c5:24:58:67 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=half firmware=5752-v3.19 latency=0 link=no module=tg3 multicast=yes port=twisted pair 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:17:31:a3:d8:3c 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```
[/LIST]

[COLOR="Blue"]More information: [lspci and lsmod]("http://paste.ubuntu-nl.org/64308/")[/COLOR]

In Gutsy (see this [_[COLOR="Blue"]thread[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=759815")), I would connect to the Internet by disabling the Network Manager, using "sudo pppoeconf", "sudo iwconfig eth1 essid GW-AP11X", then finally "pon dsl-provider". Now I cannot do any of those.

Thanks for any help! 
ilych

**EDIT:** After installing ndiswrapper (not sure how to configure it or what it is for), Driver Manager finally recognized my Broadcom driver and it is "In use" with the b43 driver, but it doesn't seem to be working. The firmware does not seem to be working (it installed one from installation CD).

---

### Post by ilych on 2008-04-25
I need to Google more often.

This thread solved my problem: [http://ubuntuforums.org/showthread.php?t=738216](http://ubuntuforums.org/showthread.php?t=738216)

Thank you, almostdvs.

---

### Post by brew1brew on 2008-04-26
try this [page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"), hope it helps, I took care of my problems. if you do have to use ndiswraper, make sure you look at the "hardy bug fix"

Les

---

