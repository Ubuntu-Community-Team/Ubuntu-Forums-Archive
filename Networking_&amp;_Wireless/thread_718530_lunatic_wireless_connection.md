---
title: "lunatic wireless connection"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by wilson79 on 2008-03-08
Hi everyone, I'm posting this as my wireless connection is working correctly... but the problem is that this happens only once in a while. Some days it won't connect at all, even though the network is detected and the signal is strong.

Nothing changes even trying the manual connection as described in the sticky post. During manual connection, the "sudo dhclient eth1" command tells me no DHCPOFFER was received.
Other laptops (and this one as well!) with XP/vista don't have any difficulty connecting automatically, as the wireless newtork is unprotected,

I'm running gutsy on an Acer Aspire 7720 Laptop dual boot with Vista, with Centrino (intel 3945ABG), the wireless network driver is supposingly installed correctly (i'm using Wicd) as it is working in this very moment.

Thanks in advance for any help...

---

### Post by jan quark on 2008-03-08
can you please post the output from these terminal commands:

```
sudo lshw -C network
```
```

iwconfig
```

```
ifconfig
```
```

sudo iwlist scan
```
```

cat /etc/network/interfaces
```

---

### Post by wilson79 on 2008-03-08
here is the output:

```

mauro@cesare-laptop:~$ sudo lshw -C network
[sudo] password for mauro:
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:6d:7c:0e
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 firmware=5787m-v3.22 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 02
       serial: 00:1c:bf:40:76:cd
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=14.0.169.98 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11b
mauro@cesare-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:80:C8:38:B4:4D   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/100  Signal level=-69 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16   Missed beacon:0

mauro@cesare-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:38:6D:7C:0E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:1C:BF:40:76:CD  
          inet addr:14.0.169.98  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe40:76cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:784 errors:0 dropped:16 overruns:0 frame:0
          TX packets:669 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:493407 (481.8 KB)  TX bytes:95164 (92.9 KB)
          Interrupt:19 Base address:0xc000 Memory:97100000-97100fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:996 (996.0 b)  TX bytes:996 (996.0 b)

mauro@cesare-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:80:C8:38:B4:4D
                    ESSID:"default"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=63/100  Signal level=-69 dBm  Noise level=-69 dBm
                    Extra: Last beacon: 248ms ago

mauro@cesare-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


```

Another example for the problem I'm facing: just after posting the thread I rebooted my machine, and it took half an hour to get the network connection back again.

---

### Post by prshah on 2008-03-08
consider adding "ipv6" to your list of blacklisted items at /etc/modprobe.d/blacklist, if you are on an ipv4 only network.

Short of that the only thing I can think of is interferance from an outside source, eg. cordless phones also use the 2Ghz spectrum that is used by wireless.

Cheers,
PRShah

---

### Post by wilson79 on 2008-03-08
> consider adding "ipv6" to your list of blacklisted items at /etc/modprobe.d/blacklist, if you are on an ipv4 only network.

Hi prshah, can you tell me how do I add it? just by adding a new line "blacklist ipv6" in the blacklist file?
ps: I noticed the following code in the blacklist file (I am completely new to linux)
```
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
```
is this line ok or could it be the cause of something?

> Short of that the only thing I can think of is interferance from an outside source, eg. cordless phones also use the 2Ghz spectrum that is used by wireless.

I really don't think that could be the cause, why else does the same pc connect flawlessly and without exception to the same network with vista? or another laptop with xp less than one foot away?
thanks a lot

---

### Post by prshah on 2008-03-09
Yes just run the command

cp /etc/modprobe.d/blacklist . && sudo echo blacklist ipv6 >> /etc/modprobe.d/blacklist

It will make a copy of the blacklist file in your home directory and add the line to the original file in /etc/...

You should be aware that the 2.4Ghz spectrum for wireless varies slightly from region to region. Maybe your router and win box are set to one region, and your linux system to another? This automatically leads to the question: How to I check/change the region, and my answer: Google is your friend.

btw, these may not be the problem agent at all; maybe as you eliminate things one by one you can finally narrow it down to something. 

Cheers,
PRShah

---

