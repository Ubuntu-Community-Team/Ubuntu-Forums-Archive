---
title: "Newby with problem getting ubuntu online"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by morgan365 on 2010-10-26
O.k. I can not get my ubuntu online i have tried all morning to get online using my ubuntu to no avail.I have tried plugging and unplugging my modem.I also went to network tools and sent a ping as it tells you in the network help section,and it says i am not connected and can't reach dns server,but i changed over to microsoft and it works fine.I have used my ubuntu online before and i don't believe i have changed anything so what could be the issue

---

### Post by Quackers on 2010-10-26
I presume you are referring to wireless? Have you tried plugging an ethernet cable in to your pc and router then running System > Admin > Additional drivers. A wireless driver may appear for installation then.

---

### Post by cariboo on 2010-10-26
Is you network card detected and is the proper driver being loaded? To check, open a terminal and type:

```
lshw -C networking
```

the output should look something like this:

```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 40:61:86:62:eb:b9
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.250 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:d800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:feae0000-feafffff(prefetchable)
```

if everything looks ok in the output, are you getting an ip address, in the same terminal type:

```
ifconfig
```

The output should look someyhing like this:

```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:62:eb:b9  
          inet addr:192.168.1.250  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fe62:ebb9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30021793 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24751290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36709821532 (36.7 GB)  TX bytes:18040750335 (18.0 GB)
          Interrupt:26 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6973 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6973 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:529934 (529.9 KB)  TX bytes:529934 (529.9 KB)
```

If you don't have an ip address in the same terminal type:

```
sudo dhclient eth0
```

I run static ip addresses, so i can't show you an example at the moment, but you should see the above command assign an ip address to you system. Once you got an ip address you should be able to connect to the internet.

---

### Post by morgan365 on 2010-10-26
No this is direct from cable line in to modem to computer no router i will be putting it on a wired router soon but i need to make sure everything is still working correct then i plan to put this computer on a router in the near future so if you could tell me any changes i need to make to get it ready would be great

---

### Post by d3v1150m471c on 2010-10-26
please tell us what version of ubuntu you are using and the output of the following commands:
```

lspci | grep "Ethernet"
ifconfig

```

---

