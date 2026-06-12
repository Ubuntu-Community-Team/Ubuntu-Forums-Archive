---
title: "Netgear WNR2000 Connection trouble in Ubuntu 14.04"
date: 2015-08-12
forum: Networking &amp; Wireless
---

### Post by squeaky2 on 2015-08-12
Hey!

My computer is having a bad day. It's a Dell HP Compaq running 14.04 Ubuntu. I could never find a NIC that could fit on the motherboard, so I use a Netgear WPN111 USB Wi-Fi key. It hasn't been updated since early July due to an extended trip that I took. The router is a Netgear WNR2000. I know for a fact that it works on my other devices. I've tried all the tips and tricks I can think of from unplugging it and plugging it back in to restarting the network manager from the terminal. All my ideas have come up dry. :( 

Here's the output that I got from running 'ifconfig', 'sudo lshw -C network', and 'route -n'.

```
ro****@ro****:~$ route -n  

 Kernel IP routing table  
 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface  
 0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan1  
 192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1  
 ro****@ro****:~$ sudo lshw -C network  
   *-network                
        description: Ethernet interface  

        product: 82566DM-2 Gigabit Network Connection  
        vendor: Intel Corporation  
        physical id: 19  
        bus info: pci@0000:00:19.0  
        logical name: eth0  
        version: 02  
        serial: 00:1c:c4:a0:c5:85  
        capacity: 1Gbit/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=1.3-1 latency=0 link=no multicast=yes port=twisted pair  
        resources: irq:42 memory:f0180000-f019ffff memory:f01a5000-f01a5fff ioport:1100(size=32)  
   *-network  
        description: Wireless interface  
        physical id: 1  
        bus info: usb@1:5  
        logical name: wlan1  
        serial: 00:22:3f:09:ba:75  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes driver=ar5523 driverversion=3.13.0-55-generic firmware=N/A ip=192.168.1.31 link=yes multicast=yes wireless=IEEE 802.11bg  
 ro****@ro****:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:1c:c4:a0:c5:85   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:19 Memory:f0180000-f01a0000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:65536  Metric:1  
           RX packets:935 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:935 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:61785 (61.7 KB)  TX bytes:61785 (61.7 KB)  
   
 wlan1     Link encap:Ethernet  HWaddr 00:22:3f:09:ba:75   
           inet addr:192.168.1.31  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::222:3fff:fe09:ba75/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:276 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:6 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:83863 (83.8 KB)  TX bytes:1024 (1.0 KB)  
 

 


```

Ideas? I could definitely use some.

---

### Post by chili555 on 2015-08-12
> My computer is having a bad day. Could you please be more specific? What is happening, or not, other than as expected?

Your device shows every sign of being connected:> wlan1     Link encap:Ethernet  HWaddr 00:22:3f:09:ba:75   
           inet addr:192.168.1.31  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::222:3fff:fe09:ba75/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:276 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:6 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:83863 (83.8 KB)  TX bytes:1024 (1.0 KB)It has an IP address and is evidently receiving and sending data.

Where or what is wlan0? Wasn't there an internal device previously? Or was wlan0 another USB that you tried and discarded in favor of the rare and elusive WNR2000.

---

### Post by squeaky2 on 2015-08-12
It isn't acknowledging any sort of connection to the internet. It is reading a connection to the house LAN, but when I try to open Firefox, or run apt-get update, it reads a bunch of error messages.
When I got my computer, there was no internal device. I had to use a different USB wifi key, and I have no idea what brand it was because the casing had been stripped and wrapped in paper to protect the chip. It worked great for a long time, but one day it just quit.

---

### Post by chili555 on 2015-08-12
>  It is reading a connection to the house LAN, but when I try to open Firefox, or run apt-get update, it reads a bunch of error messages.Let's see what the log has to say about this. Boot up, connect, apparently, and then run and post:```
dmesg | grep -e wlan -e ar5523
route -n
ping -c3 192.168.1.1
ping -c3 8.8.8.8
```Thanks.

---

### Post by squeaky2 on 2015-08-12
Never mind, found out what the problem was. Thanks for listening to an idiot, sorry to waste your time.
My brother tried tinkering with the computer and somehow got my firewall to deny outgoing packets. *facepalm*. Sorry, again. :P

---

### Post by chili555 on 2015-08-12
No worries. We're glad it's working by whatever means.

Have fun!

---

