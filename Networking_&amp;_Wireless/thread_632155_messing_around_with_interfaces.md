---
title: "messing around with interfaces"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by ziphyre on 2007-12-05
Hi,

I've been messing around with networking. And here is something I can't understand.
(By the way, I have only 1 network card)

Here is my /etc/network/interfaces file
```
ziphyre@neptune:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
```

yeah, that's all. But after a complete reboot of the system, my eth0 is up, and working, and I have a bonus eth1 interface which I'm sure I didn't configured. And this is the result of ifconfig
```

ziphyre@neptune:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:FC:CE:9A:A1  
          inet addr:10.0.0.100  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fece:9aa1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6624 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3997524 (3.8 MB)  TX bytes:1014467 (990.6 KB)
          Interrupt:17 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 80:00:60:0F:E8:00  
          inet6 addr: fe80::8200:60ff:fe0f:e800/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:634618 dropped:0 overruns:0 frame:634618
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:732 (732.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5104 (4.9 KB)  TX bytes:5104 (4.9 KB)
```

Can you please tell me where do these configurations come from. And how can I put it to the way It should be normally, ie with a proper interface file etc...

Thanks

[Ubuntu 7.10, 2.6.22-14-generic kernel]

---

### Post by salefish on 2007-12-05
Do you have a LAN? I'm somewhat new at this but I think thats what that is. I could be wrong.

---

### Post by rustybronco on 2007-12-05
> **ziphyre said:**
> Hi,
.
(By the way, I have only 1 network card)

Here is my /etc/network/interfaces file
```
ziphyre@neptune:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
```

yeah, that's all. But after a complete reboot of the system, my eth0 is up, and working, and I have a bonus eth1 interface which I'm sure I didn't configured. And this is the result of ifconfig
```

ziphyre@neptune:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:FC:CE:9A:A1            


eth1      Link encap:Ethernet  HWaddr 80:00:60:0F:E8:00  
                    RX bytes:5104 (4.9 KB)  TX bytes:5104 (4.9 KB)
```

Can you please tell me where do these configurations come from. And how can I put it to the way It should be normally, ie with a proper interface file etc...
looks like you have two ethernet ports, because of the two different mac addresses.
one on board and one card possibly?

---

### Post by ziphyre on 2007-12-06
> **rustybronco said:**
> looks like you have two ethernet ports, because of the two different mac addresses.
one on board and one card possibly?

nope, I have only 1 ethernet port. And even stranger, right now the result of ifconfig is normal. a eth0 and a lo interface. But still, my /etc/network/interfaces file is almost empty:

```
ziphyre@neptune:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
```

How does eth0 configure itself?

---

### Post by rustybronco on 2007-12-07
> **ziphyre said:**
> nope, I have only 1 ethernet port. And even stranger, right now the result of ifconfig is normal. a eth0 and a lo interface. But still, my /etc/network/interfaces file is almost empty:

```
ziphyre@neptune:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
```

How does eth0 configure itself?how about posting the results of  lshw -C network

---

### Post by ziphyre on 2007-12-07
> **rustybronco said:**
> how about posting the results of  lshw -C network

sure:

```
ziphyre@neptune:~$ sudo lshw -C network
[sudo] password for ziphyre:
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:fc:ce:9a:a1
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=10.0.0.100 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
```

---

### Post by el escocés on 2007-12-07
I googled the MAC address of eth1 and the results are interesting...

[http://www.pocketpcfaq.com/faqs/activesync/tshoot-as4x-connection.htm](http://www.pocketpcfaq.com/faqs/activesync/tshoot-as4x-connection.htm)
[http://www.modaco.com/content/Pocket-PC-General-Discussion/243878/ActiveSync-Aaaargh/](http://www.modaco.com/content/Pocket-PC-General-Discussion/243878/ActiveSync-Aaaargh/)
[http://osdir.com/ml/handhelds.ipaq.synce.general/2006-11/msg00031.html](http://osdir.com/ml/handhelds.ipaq.synce.general/2006-11/msg00031.html)

You wouldn't have a PDA connected would you?

---

### Post by ziphyre on 2007-12-07
> **el escocés said:**
> I googled the MAC address of eth1 and the results are interesting...

[http://www.pocketpcfaq.com/faqs/activesync/tshoot-as4x-connection.htm](http://www.pocketpcfaq.com/faqs/activesync/tshoot-as4x-connection.htm)
[http://www.modaco.com/content/Pocket-PC-General-Discussion/243878/ActiveSync-Aaaargh/](http://www.modaco.com/content/Pocket-PC-General-Discussion/243878/ActiveSync-Aaaargh/)
[http://osdir.com/ml/handhelds.ipaq.synce.general/2006-11/msg00031.html](http://osdir.com/ml/handhelds.ipaq.synce.general/2006-11/msg00031.html)

You wouldn't have a PDA connected would you?

Nope, nothing..
And still, how about my /etc/network/interfaces file being almost empty but eth0 still working?

---

### Post by el escocés on 2007-12-07
Did you or do you have any virtualisation programs installed?

Disable the eth1 and see if you can still connect to internet

```
sudo ifdown eth1
```

To enable it again

```
sudo ifup eth1
```

---

### Post by ziphyre on 2007-12-07
> **el escocés said:**
> Did you or do you have any virtualisation programs installed?

Disable the eth1 and see if you can still connect to internet

```
sudo ifdown eth1
```

To enable it again

```
sudo ifup eth1
```

After a reboot eth1 disappeared strangely. So for now, there is nothing to disable. ifconfig -a gives me eth0 and lo. The way it should be (or shouldn't, since I didn't specify eth0 on my /etc/network/interfaces  file)

So right now, my only question is how eth0 is up and running? (I give up on the eth1 thing)

---

### Post by njparton on 2007-12-07
Add the following line to your interface file in the section dealing with eth0, then delete all other sections apart from that for lo and restart. 

```
hwaddress ether XX:XX:XX:XX:XX
```

where XX:XX:XX:XX:XX is the mac address of your adapter.

---

### Post by MachineBucket on 2007-12-07
Did you happen to check /etc/iftab? You can specify an interface's MAC with an interface name (eth0, eth1, etc.). This way you can force a device to use a specific interface name on boot.

---

### Post by ziphyre on 2007-12-11
> **el escocés said:**
> I googled the MAC address of eth1 and the results are interesting...

[http://www.pocketpcfaq.com/faqs/activesync/tshoot-as4x-connection.htm](http://www.pocketpcfaq.com/faqs/activesync/tshoot-as4x-connection.htm)
[http://www.modaco.com/content/Pocket-PC-General-Discussion/243878/ActiveSync-Aaaargh/](http://www.modaco.com/content/Pocket-PC-General-Discussion/243878/ActiveSync-Aaaargh/)
[http://osdir.com/ml/handhelds.ipaq.synce.general/2006-11/msg00031.html](http://osdir.com/ml/handhelds.ipaq.synce.general/2006-11/msg00031.html)

You wouldn't have a PDA connected would you?

Today, when I came to the office, I saw a pda connected to my computer. Its my colleuge's pda, just charching (not synching). It seems he used to charge it on my pc, because usb ports are more confortable to reach!!!! It took a long time for him to understand why I drove crazy :)

Anyway, thanks for your guidance

---

