---
title: "[SOLVED] No IP network connectivity on wireless"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by Tony Flury on 2008-07-06
this used to work - but i then i got last weeks updates to 2.6.24-19 and everything broke :(.

I have rolled back to 2.6.24.18 - but i still can't get wireless working, and i hope someone can help me.

**_Symptoms_**
Getting Wifi connectivity, and i am being assigned an IP address. However I have no IP connectivity when connected solely via wireless. (i.e. pings do not work, web pages do not load - even DNS does not seems to work).

Wired connectivity works fine - which is how i am able to post this.

As you can see i have a Broadcom B43 chip set - which proved problematic when i first installed Ubuntu - but as i say i did get it working.

I have attached the following hopefully diagnostic outputs so someone might be able to help me :


```

uname -r

2.6.24-18-generic

```

```

sudo lshw -C network

  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:d2:ce:4b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.66 multicast=yes wireless=IEEE 802.11g

```

```

sudo ifconfig

 eth2      Link encap:Ethernet  HWaddr 00:1b:24:09:75:5f  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe09:755f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:619908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:285047619 (271.8 MB)  TX bytes:706376 (689.8 KB)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32373 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13978798 (13.3 MB)  TX bytes:13978798 (13.3 MB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:d2:ce:4b  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fed2:ce4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:342240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3417886 (3.2 MB)  TX bytes:45258115 (43.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-D2-CE-4B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

```

sudo iwconfig

lo        no wireless extensions.

eth2      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"BTHomeHub-A8AB"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:1D:68:09:9B:69   
          Bit Rate=9 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:EBD0-1CC9-B0
          Link Quality=65/100  Signal level=-64 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I have also attached the output from dmesg - in case that might help. Apologies for having to zip it

I am happy to post whatever other information might be required.

---

### Post by nixscripter on 2008-07-06
1. What do your routing tables look like (**route** command)? Your packets might be getting sent the wrong place.
2. What is eth2 in the **ifconfig** posting? I notice it has an IP address too.

---

### Post by Tony Flury on 2008-07-06
2nd question first - eth2 is my wired connection i guess - which i am using to do things like post to this forum.

```

sudo route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth2
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 eth2

```

this is with the wireless connection unplugged.

the output from route-n might be more useful - not sure ...

```

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 eth2

```

---

### Post by nixscripter on 2008-07-08
Looks like you need to set a default route.

Was that why you marked this as solved?

---

