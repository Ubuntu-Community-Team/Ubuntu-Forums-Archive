---
title: "optimize internet"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by navidson on 2009-01-02
I'm new to ubuntu and have been enjoying it greatly. Unfortunately I'm not super educated when it comes to computers. I have a dell inspiron 1525 and an n series network card. My computer came with ubuntu and ran great but I'm noticing my download speeds have greatly decreased. Is there a program like system mechanic that can optimize my computer and internet connection for me or is that simply something i will need to learn. i've tried a few things i found in forums but they haven't seemed to work. any help or advice would be appreciated.

thanks

---

### Post by Michael.Godawski on 2009-01-02
hi,

can you please post the output of these terminal commands to check if your network connection is running correctly?

```
sudo lshw -C network
iwconfig
ifconfig
```

---

### Post by amaroKer on 2009-01-02
Decreased compared to what?  Since the computer was new, or another computer entirely?

---

### Post by navidson on 2009-01-02
> **Michael.Godawski said:**
> hi,

can you please post the output of these terminal commands to check if your network connection is running correctly?

```
sudo lshw -C network
iwconfig
ifconfig
```


ryan@dell-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e5:97:39
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:c7:78:f5
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.100 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg


that was what came up from the first command 


ryan@dell-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Mitchell"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:58:EB:0A:FF   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality=77/100  Signal level:-57 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


the second one

ryan@dell-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:e5:97:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1800 (1.7 KB)  TX bytes:1800 (1.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:c7:78:f5  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5237 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3559713 (3.3 MB)  TX bytes:754461 (736.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-C7-78-F5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


when i first got the computer i had big download speeds and now they are small i already disabled the pv6 thing..i thought maybe it was transmission so i have tried vuze but still the same thing...thanks

---

### Post by amaroKer on 2009-01-10
check out [speedtest.net]("http://www.speedtest.net/") and check out your connection speed.  Divide the posted kbps by 8, and that will be the maximum of what you can expect to dl.

---

