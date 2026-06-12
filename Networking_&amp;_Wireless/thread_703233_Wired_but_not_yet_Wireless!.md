---
title: "Wired but not yet Wireless!"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by doclord on 2008-02-21
I have recently resurrected an old dual boot (Win2000) IBM T22 laptop with only 256 MB RAM and a 20 GB harddisk, to give the family extra Internet capacity.  This old cronk works remarkably well with ubuntu 7.1 (Linux ubuntu 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux).  I have a company ZyXEL (Prestige 600) router and a Cisco Aironet 350 Series PCMCIA wirless card.  The card appears to be working OK, as the green status light is flashing and the driver looks OK.  I addition, it does appear to see my neighbours BT HomeHub router!  The company router works fine with my work Windows XP laptop.  It uses WEP and does not broadcast the SSID.  If I connect my ububtu machine to the router via an ethernet cable, then all works fine.  If I build a new Windows wireless profile, using the provided SSID and WEP key, then all works fine (proving that I have the correct names, etc.).  I have played around with all the obvious ubuntu available network options, but still cannot get the wireless to work - very annoying, but I am sure that I am very close to getting this working!!
Here is the output from **ifconfig:**

```

eth0      Link encap:Ethernet  HWaddr 00:03:47:8D:CC:16  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:fe8d:cc16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4565 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6355950 (6.0 MB)  TX bytes:578291 (564.7 KB)

eth1      Link encap:Ethernet  HWaddr 00:11:20:DF:80:71  
          inet6 addr: fe80::211:20ff:fedf:8071/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:2068 dropped:0 overruns:0 frame:2068
          TX packets:92 errors:92 dropped:0 overruns:0 carrier:92
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:26337 (25.7 KB)
          Interrupt:3 Base address:0x100 

eth1:avah Link encap:Ethernet  HWaddr 00:11:20:DF:80:71  
          inet addr:169.254.7.36  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```


eth0 appears to be the working wired ethernet connection.  Not sure why there are 2 eth1's!

Please help and many thanks in advance...

---

### Post by nixscripter on 2008-02-21
I'm wondering about those two eth1 also, especially since 1 seems to have an IP and one doesn't.

Would you please post the output of:

```
iwconfig
```

---

### Post by doclord on 2008-02-21
Thanks nixscripter,

As requested, here is the output from iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-117 dBm  Noise level=-117 dBm
          Rx invalid nwid:444  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:345   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-117 dBm  Noise level=-117 dBm
          Rx invalid nwid:444  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:345   Missed beacon:0

```

---

### Post by nixscripter on 2008-02-21
Hmm. It would appear there are two network interfaces with wireless capability: eth1 and wifi0.

Are you sure you only have one wireless card in the machine? Please post the output of:

```
ifconfig eth1
ifconfig wifi0
```

Also, please put the output between two CODE tags so that things like smilies aren't interpreted (makes it harder to read).

---

### Post by rustybronco on 2008-02-21
> **doclord said:**
>   I have a company ZyXEL (Prestige 600) router and a Cisco Aironet 350 Series PCMCIA wirless card.  The card appears to be working OK, as the green status light is flashing and the driver looks OK.  I addition, it does appear to see my neighbours BT HomeHub router!  The company router works fine with my work Windows XP laptop.  **It uses WEP and does not broadcast the SSID.** 
Please help and many thanks in advance...Also try broadcasting the ESSID.

---

### Post by doclord on 2008-02-21
Thanks again nixscripter,
Arghh, code tags, didn't know about these until you pointed them out!
There is only wirless card (namely Cisco Aironet 350 Series - PCMCIA).

Here is the output from the 2 **ifconfig** commands that you requested:

```

**ifconfig eth1**
eth1      Link encap:Ethernet  HWaddr 00:11:20:DF:80:71  
          inet6 addr: fe80::211:20ff:fedf:8071/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1195 dropped:0 overruns:0 frame:1195
          TX packets:3 errors:3 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:738 (738.0 b)
          Interrupt:3 Base address:0x100

**ifconfig wifi0**
wifi0     Link encap:UNSPEC  HWaddr 00-11-20-DF-80-71-D0-E3-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:2312  Metric:1
          RX packets:0 errors:1210 dropped:0 overruns:0 frame:1210
          TX packets:3 errors:3 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 b)  TX bytes:738 (738.0 b)
          Interrupt:3 Base address:0x100 

```

Hope this helps!

---

### Post by doclord on 2008-02-21
Thanks rustybronco,
Believe me, I really would like to change the setting on the router to broadcast the ESSID.  Problem is I need the appropriate access...am working on this one!

---

### Post by nixscripter on 2008-02-21
That's odd. It looks like eth1 and wifi0 are two interfaces connected to the same device (the HWaddr is the same).

```

**ifconfig eth1**
eth1      Link encap:Ethernet  [color=red]HWaddr 00:11:20:DF:80:71[/color]
          inet6 addr: fe80::211:20ff:fedf:8071/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1195 dropped:0 overruns:0 frame:1195
          TX packets:3 errors:3 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:738 (738.0 b)
          Interrupt:3 Base address:0x100

**ifconfig wifi0**
wifi0     Link encap:UNSPEC  [COLOR="Red"]HWaddr 00-11-20-DF-80-71-D0-E3[/COLOR]-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:2312  Metric:1
          RX packets:0 errors:1210 dropped:0 overruns:0 frame:1210
          TX packets:3 errors:3 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 b)  TX bytes:738 (738.0 b)
          Interrupt:3 Base address:0x100 

```

I've never seen that before. I suspect that's the cause of the problem.

Let's see what physical device it is. Post the output of:

```
lshal
```

which will give a long list of devices, and let us see what device is providing each interface.

---

### Post by doclord on 2008-02-21
Thanks again nixscripter,
what a star you are!

As requested, I attach a file containing the output from the **lshal** command.  I had to research UNIX file compression, as the original file was too large to upload!  Anyway, the lshal.lst was reduced to an acceptable size by the gzip command!
Enjoy...

---

### Post by nixscripter on 2008-02-21
Alright, I can see the device that is responsible for the eth1, and as expected, it looks like a wireless card:

(snipped this out to make it shorter)
```


udi = '/org/freedesktop/Hal/devices/net_00_11_20_df_80_71'
  info.category = 'net.80211'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pcmcia__1__1'  (string)
  info.product = 'WLAN Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_11_20_df_80_71'  (string)
  net.address = '00:11:20:df:80:71'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  [color=blue]net.interface = 'eth1'  (string)[/color]
  net.linux.ifindex = 4  (0x4)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pcmcia__1__1'  (string)
  [color=green]net.physical_device = '/org/freedesktop/Hal/devices/pcmcia__1__1'  (string)[/color]

[color=green]udi = '/org/freedesktop/Hal/devices/pcmcia__1__1'[/color]
  info.bus = 'pcmcia'  (string)
  info.linux.driver = 'airo_cs'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_104c_ac1b'  (string)
  [color="red"]info.product = '350 Series Wireless LAN Adapter'  (string)[/color]
  info.subsystem = 'pcmcia'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pcmcia__1__1'  (string)
  info.vendor = 'Cisco Systems'  (string)

```

However, the interface wifi0 is not in the list, which means it is not being created by a physical device registered in HAL. At the moment, I can't think of where it's coming from. Do you have any sort of VPN software installed?

**UPDATE:** I think wifi0 might be a phantom interface created by the card to represent the other end of a wireless connection. I've recently see another post where a new interface had the other end's hardware address, and that was the conclusion I came to. That would mean it's not a problem if I'm right. This is just guess work, but I'm doing the best I can. If I can figure out what to do next, I'll post again.

---

### Post by doclord on 2008-02-25
Thanks again nixscripter,
Looks like we are closer, but not quite able to resolve the problem.  Any further ideas would be very much appreciated.  I do not have any VPN s/w installed.  Do you think removing the wifi0 interface might help?  If so, how would I do this? Thanks...

---

