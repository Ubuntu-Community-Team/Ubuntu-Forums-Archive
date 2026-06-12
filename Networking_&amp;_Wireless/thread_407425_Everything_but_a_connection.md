---
title: "Everything but a connection"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by mceldon on 2007-04-12
Hi,

Sorry for the repost but I reckon I need to include a few more details here, perhpas I wasn't clear enough - please help before I give up.

I cannot connect to my local network via the inbuilt laptop wireless.

I'm new to Ubuntu so treat me gently please !

OK - So this is a fresh install of Edgy Eft 6.10 - nothing touched apart from going to Admin > Networking and adding my SSID - (I've turned encyption off till I can get things going)

After refreshing the config, I try to ping anything without results - I've been through lots of posts in this forum so heres the output of the relevant commands:
```

**lshw:**

  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@06:05.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:6c:95:8e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 multicast=yes wireless=unassociated
       resources: iomemory:b8006000-b8006fff irq:50

**ifconfig:**

eth1      Link encap:Ethernet  HWaddr 00:13:CE:6C:95:8E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:31395 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6472 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0x6000 Memory:b8006000-b8006fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9876 (9.6 KiB)  TX bytes:9876 (9.6 KiB)

**iwconfig:**

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"JOYJOY"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

So I can see that 'unassociated' is probably a Bad thing. Can someone please help me with this ?

I've even attempted to install network manager from 'Add/Remove' packages but get an error saying:
```

Network Manager cannot be installed on your computer type

```

Thanks for any help,

Mac

---

### Post by mceldon on 2007-04-14
Never mind - I went Fedora 6 :)

---

