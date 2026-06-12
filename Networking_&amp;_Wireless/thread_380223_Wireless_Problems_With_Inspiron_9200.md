---
title: "Wireless Problems With Inspiron 9200"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by tcevans on 2007-03-09
Ok let me preface this by saying I am a completely newbie on the linux thing, but I'm trying it out to escape the grip of Microsoft.

Right now I am dualbooting XP Home and Ubuntu 6.10

I have a Intel ProSet Wireless 2000bg wireless card which works fine in windows, but not so much in Ubuntu.  In fact, when going through the network tools, I can't even see a list of any available networks.  The strange thing is that the card worked fine when I ran the 6.06 LiveCd.

At school, the network is not encrypted so the encryption part is not a problem for now (at home I have WPA2).  However, I cannot even see the network name, and if I manually type it in, nothing happens still.

I do have this information, and if anymore is needed, please let me know.  This is getting increasingly frustrating.

> tcevans@tcevans-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      unassociated  ESSID:"SUIC-iv"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.



> tcevans@tcevans-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:63:C7:AD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:BA:CE:00  
          inet6 addr: fe80::20e:35ff:feba:ce00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:414 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:7 Base address:0x6000 Memory:faffc000-faffcfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


---

### Post by tcevans on 2007-03-09
Here is some more relevant information:

```
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connec
tion (rev 05)
        Subsystem: Intel Corporation Unknown device 2721
        Flags: bus master, medium devsel, latency 32, IRQ 7
        Memory at faffc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

```


```
tcevans@tcevans-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:11:43:63:c7:ad
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:faffe000-faffffff irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:ba:ce:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.1.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) link=no multicast=yes wireless=unassociated
       resources: iomemory:faffc000-faffcfff irq:7
```

---

