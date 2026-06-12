---
title: "usb wireless adapter in ubuntu 9.10"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by hollowtd on 2010-01-15
So I've got a macbook 1.1 and I run Mac OS and Ubuntu 9.10 on it. I have an external USB wifi adapter that works great on my mac. However, I run it in Ubuntu and I can connect through it to the wireless signal, but when I firefox or chrome or whatever, it thinks and then doesn't load the webpage. Is there anything I can download that might help this at all? 

Cheers

Terry

---

### Post by adam814 on 2010-01-15
Depends on what your wifi chipset is.  If you could post the output of "lsusb" in a terminal it would help us point you in the right direction.

---

### Post by hollowtd on 2010-01-15
My macbook uses the Atheros AR242x wireless chipset for the airport. I'm trying to not use that and use a USB wireless adapter (that works great in Mac OS X). It's a ralink usb adapter, made my afterthemac at afterthemac.com I'm Just trying to get it to work in ubuntu 9.10 now. Cheers

---

### Post by hollowtd on 2010-01-15
i have the n300 model at the top of this page. [http://www.afterthemac.com](http://www.afterthemac.com) I'm not sure of the chipset but it works great on my macbook.

---

### Post by adam814 on 2010-01-15
Could you run this in a terminal and post the output?
```
sudo lshw -C network
```

---

### Post by superprash2003 on 2010-01-15
also post the output of
1)ifconfig
2)iwconfig

---

### Post by hollowtd on 2010-01-17
The Terminal says this:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 05ac:8240 Apple, Inc. IR Receiver [build-in]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
terry@terry-laptop:~$ lsusb
Bus 002 Device 006: ID 148f:2870 Ralink Technology, Corp. 
Bus 002 Device 005: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 002 Device 004: ID 045e:00f1 Microsoft Corp. 
Bus 002 Device 003: ID 05ac:0217 Apple, Inc. 
Bus 002 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05ac:8501 Apple, Inc. Built-in iSight [Micron]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 05ac:8240 Apple, Inc. IR Receiver [build-in]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by hollowtd on 2010-01-17
number 6 is the ralink usb wifi adapter

---

### Post by hollowtd on 2010-01-17
ifconfig in terminal spits out:

terry@terry-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:f2:30:6a:15  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4868 (4.8 KB)  TX bytes:4868 (4.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:cb:bb:b7:6f  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cbff:febb:b76f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9931 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17794518 (17.7 MB)  TX bytes:1485862 (1.4 MB)

wlan4     Link encap:Ethernet  HWaddr 00:06:4f:7f:dd:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-CB-BB-B7-6F-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster1  Link encap:UNSPEC  HWaddr 00-06-4F-7F-DD-06-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by hollowtd on 2010-01-17
and iwconfig says:

terry@terry-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"linksys-g"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:E7:8A:48   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

wmaster1  no wireless extensions.

wlan4     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by hollowtd on 2010-01-17
for sudo -c etc it says:

terry@terry-laptop:~$ sudo lshw -c network
[sudo] password for terry: 
Sorry, try again.
[sudo] password for terry: 
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 22
       serial: 00:17:f2:30:6a:15
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:26 memory:90200000-90203fff ioport:1000(size=256) memory:40000000-4001ffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:16:cb:bb:b7:6f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.107 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:90100000-9010ffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan4
       serial: 00:06:4f:7f:dd:06
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.100 multicast=yes wireless=IEEE 802.11bgn
terry@terry-laptop:~$

---

### Post by hollowtd on 2010-01-17
How do I do this. I found this in linuxquestions.org and am not sure what it means. The guy says, 
"Added this to my /etc/modprobe.d/blacklist.conf and now it works  I didn't really know what I was doing though...
Code:
blacklist rt2800usb
blacklist rt2870sta"
__

I"m not sure how he did this but if anyone can help that would be great. Sorry for all the terminal outputs. Cheers

---

### Post by hollowtd on 2010-01-17
Anyone have an idea what I need to do? I'm at a loss. I tried all the different drivers under synaptic but none of those helped. Pweez

---

### Post by hollowtd on 2010-01-17
RT2880 iNIC is a System On Chip (SoC) that integrates Ralink&#8217;s 802.11n 300 Mbps 2T3R (two transmit, three receive) Baseband and Media Access Control (MAC) chips with a MIPS4K CPU. The RT2880 supports the latest 802.11i security features including Wi-Fi Protected Setup, 802.11e Quality of Service (QoS) features including WMM and WMM-PS for prioritization of voice, video and data. It also supports both the 5GHz and 2.4GHz bands when used with Ralink&#8217;s transceivers RT2850 and RT2820, respectiveIly

THIS MIGHT BE IT BUT NOT SURE SO IS THERE A DRIVER FOR THIS?

---

### Post by adam814 on 2010-01-17
I don't know if it would help you, but those lines would be added to /etc/modprobe.d/blacklist.conf

It seems your particular adapter is supported by the rt2870sta driver.  At least according to this: [http://wiki.debian.org/rt2870sta](http://wiki.debian.org/rt2870sta)

Why blacklisting it would help you unless there's another driver for it I'm unaware of I don't know.

Is rtl2870sta loaded?  Does it show up if you run "lsmod" in a terminal?

---

### Post by hollowtd on 2010-01-17
i'm looking into this now. I'm sortof a newbie at all this so would I need to get a driver from the link you gave me. Or, what happens when I blacklist (which I don't know what that means really). Thanks so much for helping me this is a hard one

---

### Post by hollowtd on 2010-01-17
also would you recommend I download any of these from ralink itself

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

---

### Post by hollowtd on 2010-01-17
Actually when I run lsmod it does say 2870sta but under the used column it says 0

---

