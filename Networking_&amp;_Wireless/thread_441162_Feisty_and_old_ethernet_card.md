---
title: "Feisty and old ethernet card"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by Gina on 2007-05-12
I have just upgraded my old desktop PC to Feisty using a clean install onto a separate HD.  The older Dapper installation is still present on the other HD and I have dual-boot between Feisty and Dapper. 

I now find my ethernet connection doesn't work with Feisty but is still fine with Dapper.  It's an old PCI card and does 11Mb/s only.  The led on the card is on and the router shows amber, indicating an 11Mb/s connection.  The router status in Firefox also indicates that the PC is connected and shows the MAC address.  This indicates to me that the hardware is fine and that the problem is a software issue.

Does anyone have any ideas or suggestions, please?

I also have wifi but the card is not working.  It didn't in Dapper at first and needed ndiswrapper to get it going.  I will be pursuing this later but would like to get a wired connection first as messing about with wireless is much easier with a direct internet connection.

Thanks.

---

### Post by chili555 on 2007-05-12
How about letting us see:```
sudo lshw -C network
ifconfig -a
```Thanks.

---

### Post by Gina on 2007-05-12
> **chili555 said:**
> How about letting us see:```
sudo lshw -C network
ifconfig -a
```Thanks.Thanks for your prompt reply :)

Here are the results> gina@ubuntu:~$ sudo lshw  -C network
Password:
  *-network:0             
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:00:21:ce:22:5a
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 latency=0 multicast=yes
       resources: ioport:e000-e01f irq:5
  *-network:1
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 14
       bus info: pci@00:14.0
       logical name: ra0
       version: 01
       serial: 00:11:50:15:8d:47
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=32 link=yes multicast=yes wireless=RT2500 Wireless
       resources: iomemory:e6400000-e6401fff irq:10

gina@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:21:CE:22:5A  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2018 (1.9 KiB)  TX bytes:1779 (1.7 KiB)
          Interrupt:5 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

ra0       Link encap:Ethernet  HWaddr 00:11:50:15:8D:47  
          inet6 addr: fe80::211:50ff:fe15:8d47/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1172440 (1.1 MiB)
          Interrupt:10 Base address:0xc000 

gina@ubuntu:~$ 

---

### Post by Gina on 2007-05-12
No further forward here :(  The above seems to me to show the computer and router are exchanging data.  Also, when I was in the room where the router is, I noticed the connection led flashing - indicating data transfer.  However, Firefox will not connect to router admin URL (192.168.0.1) or internet and Ping reports "network unreachable".

---

### Post by chili555 on 2007-05-12
What happens when you do:```
sudo dhclient eth0
```You don't have to post the whole output, just 'no offers' or 'bound to 192.xx' will be fine. Thanks.

---

### Post by Gina on 2007-05-13
I get "bound to 192.168.0.6 - - renewal in 106751 seconds"

Looks like it's talking to the router and getting replies.  The router has allocated the LAN IP and the PC is showing it.  Accessing the router from my laptop shows devices connected, newer desktop (also running Feisty), laptop (ditto) and the old desktop - allocated 192.168.0.6 

OK...  Going to try ping again.  Back shortly....

Later....  Eureka!!  Ping working so tried Firefox and it's working :):)

That fixed it :)  Thank you very much :):)

---

### Post by chili555 on 2007-05-13
I wish they were all so easy! Does the connection survive a reboot?

Are you ready to get your wireless going? It will be almost as easy, I think.

---

