---
title: "Wired connection not working"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by mralistair on 2008-08-23
I have installed the latest hardy heron ubuntu but am not able to connect to my router, either through wired or wireless. the machine is an acer travelmate 2500. I was once able to connect wired and installed some drivers for the wireless but since then nothing has worked to connect.

I'm new too all this and have tried a few things recommended elsewhere like disabling IPv6 but nothing seems to work, the router is netgear WG834GT and i have no trouble connecting with mac or xp. routers IP is 192.168.0.1 and even if i set ip manually it still cannot connect. currently it is set to DHCP.

result of ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0a:e4:57:c6:77  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xa000 

eth0:avahi Link encap:Ethernet  HWaddr 00:0a:e4:57:c6:77  
          inet addr:169.254.8.67  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4304 (4.2 KB)  TX bytes:4304 (4.2 KB)


result of lshw -C network

  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:57:c6:77
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:6b:4b:04:f6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


all help gratefully received

---

### Post by Sam Lars on 2008-08-23
Could you do a
```
sudo dhclient eth0
```
It will try to get an IP address (which it appears isn't working).  Could you post what it says?

---

### Post by mralistair on 2008-08-24
thanks for looking

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:0a:e4:57:c6:77
Sending on   LPF/eth0/00:0a:e4:57:c6:77
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

so could this be a router problem?

---

### Post by Sam Lars on 2008-08-24
I have some cards with the same wireless chipset, so I know how to (probably) get that working.
It doesn't look like the wireless is showing up at all in ifconfig.
I guess it could be a router problem, but didn't you say you had no troubles with XP?
Do you remember what you did to install wireless drivers?
Also, could you post your /etc/network/interfaces file?

---

### Post by bsh on 2008-08-25
disable the avahi daemon as the first step. then configure eth0 manually.

---

### Post by mralistair on 2008-08-25
Sam

The wireless isn't my problem at the moment (though it will be) it's wired one that's not working.

- worked fine under xp

- interfaces file:
auto lo
iface lo inet loopback


Bsh
How would i go about that?

---

### Post by Kevbert on 2008-08-25
Regarding wireless, have you installed any firmware drivers ?  You should have a couple of directories in your /lib/firmware directory for Broadcom wireless (these may be /b43 and /b43legacy).

---

### Post by mralistair on 2008-08-25
I haven't been able to install these because of having no connection... is there an easy way to download the drivers on a different machine and move them across?
EDIT: i found folders called b43 in lib/nodules/2.6.24-19-generic/kernal/drivers/wireless

and
sys/bus
sys/modules
and usr/src/....

---

### Post by Kevbert on 2008-08-25
Have a look and one of my old [[COLOR="Red"]posts[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13"), the files are there.

---

### Post by ooolongT on 2008-08-25
I am having a similar problem, that I have thus far been unable to resolve.  If anyone is willing to take a look at my posts it is [here]("http://ubuntuforums.org/showthread.php?p=5663558#post5663558").

I have been getting great help from pytheas22, but if anyone has other advice it would be greatly appreciated. 

Good luck mralistair!

---

### Post by mralistair on 2008-08-31
a lot of the above advice seems to be for wireLESS problems.. is it likely to be the same cause as my wirED problem?

i am going to do a clean install and see what happens

---

