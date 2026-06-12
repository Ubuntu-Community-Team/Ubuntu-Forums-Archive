---
title: "Manual Wireless Configuration Works, but not KNetworkManager nor KWiFiManager"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by Sir Chasm on 2008-01-04
I'll start from the very beginning - installed a command line system, loaded up KDE and everything I wanted myself (very proud of that as I am a n00b), installed the bcm43xx driver, and tried to connect via KNetworkManager and KWiFiManager. No dice. KNetworkManager either fails at "configuring device" or at "configuring IP address". KWiFiManager sees all the networks (so does KNetworkManager), but instead of connecting just sits there searching for my essid. So then I tried connecting through the command line, namely by running:

```

sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "ESSID"
sudo iwconfig eth1 key MYKEY
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

```

which connected fine. Immediately, KWiFiManager showed that I was connected, although KNetworkManager didn't recognize. I thought that because KWiFiManager "woke up" meant that it would connect in the future, but nope. I tried again later and I am only able to connect through the command line. Does anyone know why???

extra info for those that might ask for it:

```

dima@zv5410:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:4a:3b:c3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:a5:36:79
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=192.168.0.101 latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11                                                                            b/g

```

My /etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
#auto eth1
#iface eth1 inet dhcp

#iface eth1 inet dhcp
#wireless-essid VVV
#wireless-key s:362412babadedababadedababa

#auto eth1

```

iwlist scan works fine too:
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1B:11:67:5A:E5
                    ESSID:"VVV"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=97/100  Signal level=-42 dBm  Noise level=-67 dBm
                    Extra: Last beacon: 40ms ago

```

```

dima@zv5410:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:4A:3B:C3
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x2800

eth1      Link encap:Ethernet  HWaddr 00:90:4B:A5:36:79
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fea5:3679/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14088 errors:0 dropped:4147 overruns:0 frame:0
          TX packets:12462 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8140705 (7.7 MB)  TX bytes:2640054 (2.5 MB)
          Interrupt:11 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

This is a laptop that will be moved from place to place, so it's fairly important that I get those GUI tools working, because I don't want to keep running the commands every time I come to school (every day) and home (everyday). So anything I can do?

---

### Post by Digger78 on 2008-01-04
edit your /etc/network/interfaces

```
sudo kdesu kate /etc/network/interfaces

```
add the following (replace the X's with the correct value)

```
iface eth1 inet dhcp
wireless-essid XXXXXXX
wireless-key XXXXXXXX   ([COLOR="Red"]without s:[/COLOR])

auto eth1
```

restart networking to see if it connects

```
sudo /etc/init.d/networking restart
```

I assume your home and school networks use different essid's and keys? not sure how to configure it for 2 different networks.


HTH

---

### Post by Sir Chasm on 2008-01-04
Edit #3: 

That sorta worked. I am now connected automatically to my home essid as soon as I log in. However, now KNetworkManager stopped showing any other wireless network when I right-click on it. So by solving one issue, I run into the other that when I configure KNetworkManager this way, I am only able to use one network, and are unable to switch between available networks.

---

### Post by kevdog on 2008-01-04
I wouldnt add that additional info in your interfaces file -- thats just a form of manual configuration.  If the two K wifi products are not working for you, possibly I would consider wicd.  It provides a GUI, tray icon, and it works very similar to the command line.  Here is where you can find it:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

This product is very well supported in the ubuntu forums.

---

### Post by Digger78 on 2008-01-04
you could always configure your home network to use the same essid and key ;)

im sure somebody will have a better solution though.

---

### Post by Sir Chasm on 2008-01-05
> **kevdog said:**
> I wouldnt add that additional info in your interfaces file -- thats just a form of manual configuration.  If the two K wifi products are not working for you, possibly I would consider wicd.  It provides a GUI, tray icon, and it works very similar to the command line.  Here is where you can find it:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

This product is very well supported in the ubuntu forums.

Thanks! wicd works perfectly. And it's actually quite a bit nicer than both Kwifimanager and knetworkmanager. I wish it'd have a system tray icon tho.

---

### Post by kevdog on 2008-01-05
It does have a system tray icon.  Read the documentation -- its in there.  You start /opt/wicd/tray.py

---

