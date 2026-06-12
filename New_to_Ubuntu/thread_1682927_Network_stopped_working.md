---
title: "Network stopped working"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by travmanx on 2011-02-06
/etc/network/interfaces

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.168.1.120
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1

```

lshw
```
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth1
       serial: 80:00:60:0f:e8:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=169.254.2.2 link=yes multicast=yes

```

ifconfig

```
 eth0      Link encap:Ethernet  HWaddr 00:1a:a0:8a:b3:2b  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe8a:b32b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13133 (13.1 KB)  TX bytes:10556 (10.5 KB)
          Interrupt:20 Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14004 (14.0 KB)  TX bytes:14004 (14.0 KB)


```

---

### Post by Zill on 2011-02-06
travmanx:  I'm not too sure what is going on here but your /etc/network/interfaces and ifconfig both refer to eth0 but lshw refers to eth1.  Have you got two network cards fitted - maybe one on the motherboard and one in a PCI slot?  If so then you may need to disable one in the BIOS.

Alternatively, you may like to take a look at the /etc/udev/rules.d/70-persistent-net.rules file.  I believe this should link the network card MAC address to the interface name.  I guess this could be edited to show the correct interface logical name (eth0?), followed by a reboot.  I strongly recommend backing up this file before modifying it so that you can always restore it if things go wrong!

Caveat:  I have never modified this file and so my comments may be worthless ;-)

See [Network Configuration]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html") for more info.

---

### Post by travmanx on 2011-02-06
> **Zill said:**
> travmanx:  I'm not too sure what is going on here but your /etc/network/interfaces and ifconfig both refer to eth0 but lshw refers to eth1.  Have you got two network cards fitted - maybe one on the motherboard and one in a PCI slot?  If so then you may need to disable one in the BIOS.

Alternatively, you may like to take a look at the /etc/udev/rules.d/70-persistent-net.rules file.  I believe this should link the network card MAC address to the interface name.  I guess this could be edited to show the correct interface logical name (eth0?), followed by a reboot.  I strongly recommend backing up this file before modifying it so that you can always restore it if things go wrong!

Caveat:  I have never modified this file and so my comments may be worthless ;-)

See [Network Configuration]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html") for more info.
The eth0 eth1 was my bad. When I plug my phone into charge, it runs as a modem. However when i take it out, it goes back to eth0. But it's like eth0 is non exsisting

---

### Post by electroken on 2011-02-07
I wonder if you have a static ip address on eth0 and the router is set to use dhcp. I am only throughing this out to you as a possible place to look as I am not very versed in networking myself.
Probably not a factor is it? I think I have a printer on my network with a static ip but then I thought I was told it had to be a certain address or would cause problems sometimes. Perhaps had to be above another address or outside the list of addresses that dhcp could assign I think. Not sure about this.

---

### Post by Zill on 2011-02-07
> **travmanx said:**
> The eth0 eth1 was my bad. When I plug my phone into charge, it runs as a modem. However when i take it out, it goes back to eth0. But it's like eth0 is non exsisting
So, just to clarify things for my aged brain(!), is your PC/Laptop using a phone as a modem, connected via an ethernet cable?  If not then please advise your exact connection.

Either way, with your system in its "normal" configuration (i.e. modem/router online) to connect to the internet, please confirm that the outputs you showed in your [first post]("http://ubuntuforums.org/showpost.php?p=10434520&postcount=1") are still correct.  If any are different then please post the appropriate output(s).

Please also post outputs from the following three commands:
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
```
route -n
```
```
cat /etc/resolv.conf
```

---

### Post by travmanx on 2011-02-07
> **Zill said:**
> So, just to clarify things for my aged brain(!), is your PC/Laptop using a phone as a modem, connected via an ethernet cable?  If not then please advise your exact connection.

Either way, with your system in its "normal" configuration (i.e. modem/router online) to connect to the internet, please confirm that the outputs you showed in your [first post]("http://ubuntuforums.org/showpost.php?p=10434520&postcount=1") are still correct.  If any are different then please post the appropriate output(s).

Please also post outputs from the following three commands:
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
```
route -n
```
```
cat /etc/resolv.conf
```


cat /etc/udev/rules.d/70-persistent-net.rules
```
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1a:a0:8a:b3:2b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"



```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```



cat /etc/resolv.conf
```
# Generated by NetworkManager

```

/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.168.1.120
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1

```

lshw
```
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:8a:b3:2b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=full firmware=1.1-2 ip=192.168.1.120 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:41 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:ff00(size=32)

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:8a:b3:2b  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe8a:b32b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:87349 (87.3 KB)  TX bytes:9256 (9.2 KB)
          Interrupt:20 Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:817 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66324 (66.3 KB)  TX bytes:66324 (66.3 KB)


```


eth1 popped up in previous post because my phone was plugged in via USB.

---

### Post by Zill on 2011-02-07
travmanx:  It will help resolution if you answer the question I asked in my earlier post "...is your PC/Laptop using a phone as a modem, connected via an ethernet cable? If not then please advise your exact connection."

If you are using a DSL router then your output data seems OK to me! What exactly is the problem?  Can you ping the router gateway:
```
ping 192.168.1.1
```

---

### Post by travmanx on 2011-02-07
No, as I said before, I had my cell phone plugged into the USB during the time of using those commands. Thats why that poppedup

I have Atlantic Broadband Cable.

Shouldn't resolv.conf have my DNS info in it?


And  I can connect to my router fine... It's just the "outside world" that I can't connect to.

---

### Post by Zill on 2011-02-08
> **travmanx said:**
> ...I have Atlantic Broadband Cable.

Shouldn't resolv.conf have my DNS info in it?...
I use an ADSL router and so my DNS server addresses are stored *in* the router.  In my case, resolv.conf simply points to the router.

If your cable modem/router is also configured with the DNS server addresses then I suggest you should edit (with sudo) your /etc/resolv.conf in a similar way by adding this line:
```
nameserver 192.168.1.1
```
If your cable modem/router does *not* hold the DNS info then you could try adding these directly to the resolv.conf file eg:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```
Restart network after changes with
```
sudo /etc/init.d/networking restart
```

---

