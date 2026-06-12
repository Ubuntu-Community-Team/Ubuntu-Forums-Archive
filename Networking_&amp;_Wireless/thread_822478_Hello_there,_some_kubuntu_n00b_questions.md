---
title: "Hello there, some kubuntu n00b questions"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by eru777 on 2008-06-08
I tried kubuntu with wubi (Kubuntu 8.04 with KDE) and did so after having experience with windows and networking in general.
So what I'd like to know is how to set my IP settings in kubuntu. I know I have internet but ifconfig shows an ip that doesn't exist and a mask of 255.0.0.0 . How can I change that using terminal?
I tried ifconfig and it showed me these strange values (that I just said) , moreover it doesn't ping sites.
Additionally, I can't "see" my router by adding 192.168.1.1 in the Konqueror browser.

Another thing I want to ask is : Will I experience loss of data if I plug in my Ipod ?

Thanks

---

### Post by chili555 on 2008-06-08
This:> I know I have internetand this:> it doesn't ping sites.are in conflict. If you cannot surf the web, nor even ping sites, you do not have the internet, yet. You may have a placeholder address, 169.254.boo.hoo, but you do not yet have the internet. 

Are you trying to configure wired or wireless? Is a driver loaded for your device? All of these questions, and more, will be answered with:```
sudo lshw -C network
```Then tell us whether you want wired or wireless to come to life and we'll be glad to help.

---

### Post by eru777 on 2008-06-08
When I said I have internet I mean I have a working network connection . Hence my typing here, through a dual boot PC with Windows XP and Kubuntu .

Now when I typed  
```
sudo lshw -C network
``` it said
```
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.12.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status
        -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
```

When I typed in sudo dhclient :
```
 
ermis@ubuntu:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:e6:97:63:33
Sending on   LPF/eth0/00:16:e6:97:63:33
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I have an ethernet cable connected from a router to my network card . Now for the drivers, I think that no drivers are updated, because I don't have internet in the kubuntu OS. I am using kubuntu from a dual boot (wubi) so it probably uses some of my windows drivers (?) Sorry if that was wrong, I am an ubuntu newbie.

---

### Post by chili555 on 2008-06-08
```
sudo lshw -C network
```Did you type all in one line in a terminal and then press enter?

---

### Post by eru777 on 2008-06-08
```


 *-network
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:16:e6:97:63:33
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=1.1-0 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
```

---

### Post by chili555 on 2008-06-08
May I see the result of these two commands:```
sudo ifdown eth0 && sudo ifup -v eth0
ifconfig
```Thanks.

---

### Post by eru777 on 2008-06-08
```
eth0      Link encap:Ethernet  HWaddr 00:16:e6:97:63:33
          inet6 addr: fe80::216:e6ff:fe97:6333/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:348 (348.0 B)  TX bytes:5133 (5.0 KB)
          Base address:0xd400 Memory:fb000000-fb020000

eth0:avahi Link encap:Ethernet  HWaddr 00:16:e6:97:63:33
          inet addr:169.254.6.51  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Base address:0xd400 Memory:fb000000-fb020000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:592 (592.0 B)  TX bytes:592 (592.0 B)

ermis@ubuntu:~$
```

---

### Post by chili555 on 2008-06-08
And how about:```
sudo ifdown eth0 && sudo ifup -v eth0

```All on one line, then press enter, please.

---

