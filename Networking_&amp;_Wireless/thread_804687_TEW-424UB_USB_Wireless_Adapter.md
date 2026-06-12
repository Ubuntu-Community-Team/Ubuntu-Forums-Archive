---
title: "TEW-424UB USB Wireless Adapter"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by tompouce on 2008-05-23
Hi!

I would like to know how can I use ubuntu's default wireless thingies with my usb adapter?

I don't have ndiswrapper, nor any windows drivers. But it is a part of the wlan-ng package I think. How could I use it?


Thanks!

---

### Post by bwhite82 on 2008-05-23
Need more information. What is the make and model number of the device? And my apologies, but I do not know what "wireless thingies" are. You can use Google for research simply include three terms in your search:

make model ubuntu

---

### Post by tompouce on 2008-05-23
> **Soldierboy said:**
> Need more information. What is the make and model number of the device? And my apologies, but I do not know what "wireless thingies" are. You can use Google for research simply include three terms in your search:

make model ubuntu

I meant default apps that are managing wireless connections.

Also the model number is in the title:
TrendNet Wireless Adapter: TEW-424UB


Thanks :)

---

### Post by bwhite82 on 2008-05-23
[http://ubuntuforums.org/showthread.php?t=529090](http://ubuntuforums.org/showthread.php?t=529090)

Windows drivers (for use with NDISWrapper) can be found here: [http://downloads.trendnet.com/TEW-424UB/Driver/Driver_TEW-424UB.zip](http://downloads.trendnet.com/TEW-424UB/Driver/Driver_TEW-424UB.zip)

---

### Post by tompouce on 2008-05-23
Hi again, I installed ndiswrapper and also the drivers for my usb adapter.

Install successful. But now the problem is when I do:

iwlist wlan0 scan

device does not support scanning

or

iwconfig

there's no wifi devices.

What's wrong? Thanks!

---

### Post by bwhite82 on 2008-05-23
> **tompouce said:**
> Hi again, I installed ndiswrapper and also the drivers for my usb adapter.

Install successful. But now the problem is when I do:

iwlist wlan0 scan

device does not support scanning

or

iwconfig

there's no wifi devices.

What's wrong? Thanks!

Post here, the output of the command:
> ifconfig -a

---

### Post by tompouce on 2008-05-23
eth0      Link encap:Ethernet  HWaddr 00:90:27:66:d5:7f  
          inet addr:192.168.0.153  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:27ff:fe66:d57f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7916491 (7.5 MB)  TX bytes:599276 (585.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9000 (8.7 KB)  TX bytes:9000 (8.7 KB)


:S

tom@tombox:~/Desktop$ sudo ndiswrapper -l
[sudo] password for tom: 
net8187b : driver installed
        device (0BDA:8189) present


tom@tombox:~/Desktop$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000  
tom@tombox:~/Desktop$

tom@tombox:~/Desktop$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000  
tom@tombox:~/Desktop$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth0
       version: 08
       serial: 00:90:27:66:d5:7f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.0.153 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

---

