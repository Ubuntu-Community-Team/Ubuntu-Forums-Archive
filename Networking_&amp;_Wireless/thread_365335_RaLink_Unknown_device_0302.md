---
title: "RaLink Unknown device 0302"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by whayong on 2007-02-19
Hi there!  I've failed at getting the wifi to work in the PCG-SRX77 twice now.  The first time was with a Prism54 chipset so I decided to buy a "supported" wireless card.  I got myself a MSI MP54G5 which according to this:

[https://www.fsf.org/resources/hw/net...ess/cards.html](https://www.fsf.org/resources/hw/net...ess/cards.html)

and this 

[http://ralink.rapla.net/](http://ralink.rapla.net/)

should be based on the supported RT2500 chipset.  Whenever I do ifconfig however, I get this:
```

wlan0     Link encap:Ethernet  HWaddr 00:13:D3:7C:DD:4
wlan0     Link encap:Ethernet  HWaddr 00:13:D3:7C:DD:43  
          inet6 addr: fe80::213:d3ff:fe7c:dd43/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:13584 (13.2 KiB)
          Base address:0xc000 

wmaster0  Link encap:UNSPEC  HWaddr 00-13-D3-7C-DD-43-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xc000 3  
          inet6 addr: fe80::213:d3ff:fe7c:dd43/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:13584 (13.2 KiB)
          Base address:0xc000 

wmaster0  Link encap:UNSPEC  HWaddr 00-13-D3-7C-DD-43-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xc000 
```

lspci -v

```
01:05.0 Network controller: RaLink Unknown device 0302
        Subsystem: Micro-Star International Co., Ltd. Unknown device b833
        Flags: bus master, slow devsel, latency 64, IRQ 9
        Memory at f4108000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>
```

The posts in the forums however seem to say that this card should use the RT61 driver instead.  I've tried both how to's for the RT61 and RT2500 numerous times each with fresh installs in between but can't seem to get it to work.  So here I am again, another fresh install later, waiting for some help.

BTW, here is iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"MAKS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.
```

---

### Post by whayong on 2007-02-20
OK, i used 

sudo update-pciids

Now I've got an RT2561/RT61 chipset according to lspci.  

I just need to get the damn thing working now.......

---

