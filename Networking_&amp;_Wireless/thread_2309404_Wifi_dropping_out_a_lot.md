---
title: "Wifi dropping out a lot"
date: 2016-01-10
forum: Networking &amp; Wireless
---

### Post by Gottier on 2016-01-10
Computer is a Dell Inspiron 3647 running Ubuntu 14.04.

I do have wifi, but it drops out a lot.

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr f8:bc:12:7e:a7:52  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5119703 (5.1 MB)  TX bytes:5119703 (5.1 MB)

wlan0     Link encap:Ethernet  HWaddr 90:48:9a:24:18:1b  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9248:9aff:fe24:181b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:771347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:279868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1090987653 (1.0 GB)  TX bytes:32095574 (32.0 MB)
```

/etc/network/interfaces:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

lshw -C network:

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 0c
       serial: f8:bc:12:7e:a7:52
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:e000(size=256) memory:f7d00000-f7d00fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 90:48:9a:24:18:1b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-74-generic firmware=N/A ip=192.168.1.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f7c00000-f7c7ffff memory:f7c80000-f7c8ffff
```

How come wlan0 not appearing in /etc/network/interfaces? I thought I would try to make the wlan0 network connection static, as this has helped with issues on some other computers. I was surprised there was no wlan0 in the interfaces file, and don't know what is going on, or what to do now.

---

### Post by Hadaka on 2016-01-10
Hi, your /etc/network/interfaces file is correct because you are using
NerworkManager to manage your network, if you were to configure
/etc/network/interfaces to manage your network then you would need to
remove NetworkManager as there would be a conflict.  This is correct.
```
auto lo
iface lo inet loopback
```
*See the attached to use a static connection with NetworkManager

This may help your disconnects.
```
sudo modprobe -rfv ath9k
sudo modprobe ath9k nohwcrypt=1

```
Dont boot, and see if it helps..to make permanent do..
```
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
```
also set IPv6 to IGNORE see attached:
[ATTACH=CONFIG]266647[/ATTACH][ATTACH=CONFIG]266648[/ATTACH]

---

### Post by Gottier on 2016-01-10
> **Hadaka said:**
> Hi, your /etc/network/interfaces file is correct because you are using
NerworkManager to manage your network, if you were to configure
/etc/network/interfaces to manage your network then you would need to
remove NetworkManager as there would be a conflict.  This is correct.
```
auto lo
iface lo inet loopback
```
*See the attached to use a static connection with NetworkManager

This may help your disconnects.
```
sudo modprobe -rfv ath9k
sudo modprobe ath9k nohwcrypt=1

```
Dont boot, and see if it helps..to make permanent do..
```
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
```
also set IPv6 to IGNORE see attached:
[ATTACH=CONFIG]266647[/ATTACH][ATTACH=CONFIG]266648[/ATTACH]

The two modprobe commands make the internet disconnect altogether. I have to reboot to get it working again.

---

### Post by Hadaka on 2016-01-10
Hi, the first command removes the module and the second command
inserts it with a parameter change. Do the last command and see if
that helps with the disconnects. please do..
```
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
```
thanks.

---

### Post by Gottier on 2016-01-11
> **Hadaka said:**
> Hi, the first command removes the module and the second command
inserts it with a parameter change. Do the last command and see if
that helps with the disconnects. please do..
```
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
```
thanks.

I did that, but still having problems. I bought a new USB wifi adapter, and will attempt to get it working tonight. It is this one:  
[h=1][[SIZE=2][FONT=arial]TP-LINK TL-WN722N[/FONT][/SIZE]]("http://amazon.com/gp/product/B002SZEOLG")[/h]
I suppose I just plug it and see if Ubuntu recognizes it exists as a wifi adapter, or is there something else I should do?

---

### Post by Hadaka on 2016-01-11
Hi,The usb might plug and play or it may not. If you have
decided to abandon your ath9k dirver problem,then please mark
this thread solved. Open a new thread if your usb fails. I would suggest
you go here-> [http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)
read the instructions and post your wireless-info.txt file that is created in your home directory.
thanks

---

### Post by shaun24 on 2016-02-18
This seemed to make mine drop out less but still does frequently

---

### Post by goofprog on 2016-02-18
I had this problem with my Dell too.  I replaced the driver several times and it did not work.  I had to use a high gain antenna because the signal strength was too low and kept disconnecting.

---

