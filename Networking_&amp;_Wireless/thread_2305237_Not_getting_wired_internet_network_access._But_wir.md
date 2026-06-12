---
title: "Not getting wired internet network access. But wireless connection works"
date: 2015-12-04
forum: Networking &amp; Wireless
---

### Post by Rajeesh_John on 2015-12-04
Greetings....

              I installed Ubuntu 15.10 last week and have been accessing the internet using a netgear router (wireless method...using ). Yesterday, I removed the wireless dongle (which i used to access netgear wireless) and connected an ethernet cable directly to my system. Ubuntu is listing my network adapter when i try **sudo lshw -C network****, **but when I try **pppoeconf**, it cannot find it. I believe in order to set the internet we have to use pppoeconf command. The green light on Netgear router too shows that my computer is connected. I would really appreciate it if someone could help...thank you.

I am new to Ubuntu (linux in general :D)...

_Results for_ : 

[B]sudo lshw -C network
[/B]
```

*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 06
       serial: 94:de:80:9c:26:80
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:26 ioport:de00(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:2
       logical name: wlxc0a0bbb644ef
       serial: c0:a0:bb:b6:44:ef
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.2.0-19-generic firmware=0.29 ip=192.168.0.2 link=yes multicast=yes wireless=IEEE 802.11bgn


```

---

### Post by praseodym on 2015-12-04
Change the driver via:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.040.00-1_all.deb
sudo dpkg -i *.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot

---

### Post by einpreusseinbayern on 2015-12-04
> **Rajeesh_John said:**
> Greetings....
  [..]I believe in order to set the internet we have to use pppoeconf command. [..]


usually not. The router should do this for you, just as it did when you were using wifi.

1.) make sure your NIC got a correct IP adress: ifconfig
2.) make sure your default route is set correctly: netstat -rn

---

### Post by Rajeesh_John on 2015-12-07
> **praseodym said:**
> Change the driver via:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.040.00-1_all.deb
sudo dpkg -i *.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot

I've tried your method, but it still does not work...the wired connection is still out. I can only connect to my router using wifi dongle. I installed windows on my machine and the result is the same -> wired connection not working...wifi connection works.

---

### Post by Rajeesh_John on 2015-12-07
> **einpreusseinbayern said:**
> usually not. The router should do this for you, just as it did when you were using wifi.

1.) make sure your NIC got a correct IP adress: ifconfig
2.) make sure your default route is set correctly: netstat -rn


This is the result of  [B]ifconfig

```

enp2s0    Link encap:Ethernet  HWaddr 94:de:80:9c:26:80  
          inet6 addr: fe80::96de:80ff:fe9c:2680/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:28670 (28.6 KB)
          Interrupt:26 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:151739 (151.7 KB)  TX bytes:151739 (151.7 KB)


```
[/B]

And this is the result of **netstat -rn**

```

[B]Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface[/B]

```



don't know what is wrong here....The situation is the same in Windows too... if someone sees anything weird in the command outputs please let me know (or a solution would be even better :D)

---

### Post by morozov2 on 2016-03-06
I've had the same problem with ethernet connection. I went to the BIOS and check all tabs. In one of them I found field "Network stack" it was disabled. I enabled it, and after restart I can use an ethernet connection.

---

