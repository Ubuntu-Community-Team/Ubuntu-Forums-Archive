---
title: "Can't connect to network"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by jdimstrbean on 2006-07-20
Hello,

I just installed Ubuntu 6.06(I'm new to linux) last night and am unable to connect to the internet. I'm on a university network in the apartments. On my Mac or Windows, I just plug in the ethernet and it works fine, connects DHCP. When I boot up Ubuntu, I cannot ping any sites.

I've searched through these forums but have been unable to find a solution. 

Here's my ifconfig...
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:85:85:23:DE
          inet addr:192.168.0.114  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe85:23de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:50711 (49.5 KiB)  TX bytes:18706 (18.2 KiB)
          Interrupt:209

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)
```

I came across this which seemed like it might be the issue...
```

$ dmesg | grep eth
[4294671.898000] Driver 'sd' needs updating - please use bus_type methods
[4294687.001000] skge eth0: addr 00:14:85:85:23:de
[4294687.998000] skge eth0: enabling interface
[4294689.685000] skge eth0: Link is up at 100 Mbps, full duplex, flow control tx and rx
[4294692.150000] skge eth0: disabling interface
[4294692.152000] skge eth0: enabling interface
[4294693.839000] skge eth0: Link is up at 100 Mbps, full duplex, flow control tx and rx
[4294722.212000] eth0: no IPv6 routers present
```

Could this be the problem? Tried searching for "Driver 'sd'" but could not come up with a solution. Any ideas? 

Thanks in advance.

---

### Post by wahman143 on 2006-07-20
> **jdimstrbean said:**
> Hello,

I just installed Ubuntu 6.06(I'm new to linux) last night and am unable to connect to the internet. I'm on a university network in the apartments. On my Mac or Windows, I just plug in the ethernet and it works fine, connects DHCP. When I boot up Ubuntu, I cannot ping any sites.

I've searched through these forums but have been unable to find a solution. 

Here's my ifconfig...
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:85:85:23:DE
          inet addr:192.168.0.114  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe85:23de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:50711 (49.5 KiB)  TX bytes:18706 (18.2 KiB)
          Interrupt:209

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)
```

I came across this which seemed like it might be the issue...
```

$ dmesg | grep eth
[4294671.898000] Driver 'sd' needs updating - please use bus_type methods
[4294687.001000] skge eth0: addr 00:14:85:85:23:de
[4294687.998000] skge eth0: enabling interface
[4294689.685000] skge eth0: Link is up at 100 Mbps, full duplex, flow control tx and rx
[4294692.150000] skge eth0: disabling interface
[4294692.152000] skge eth0: enabling interface
[4294693.839000] skge eth0: Link is up at 100 Mbps, full duplex, flow control tx and rx
[4294722.212000] eth0: no IPv6 routers present
```

Could this be the problem? Tried searching for "Driver 'sd'" but could not come up with a solution. Any ideas? 

Thanks in advance.
What is the output of:
```

$ sudo cat /etc/resolv.conf

```

In addition, can you ping by IP Address (ie - Google is 64.233.187.104?

---

### Post by jdimstrbean on 2006-07-20
Here's the output

```
nameserver 192.168.0.1
```

I can't ping by IP. it just hangs after
```

PING 64.233.187.104 (64.233.187.104) 56(84) bytes of data.
```

---

### Post by wahman143 on 2006-07-20
oops - typo - try 64.233.187.99.  Sorry about that...just trying to see if this is a DNS issue or not.

Do you use a router, or are you directly on a cable modem (I would assume router based on your /etc/resolv.conf)?

---

### Post by jdimstrbean on 2006-07-20
Can't ping any ip that i've tried. Ethernet just plugs into the wall. I live in an apartment off of the University. I think it just goes to the school's T1 line.

---

### Post by wahman143 on 2006-07-20
> **jdimstrbean said:**
> Can't ping any ip that i've tried. Ethernet just plugs into the wall. I live in an apartment off of the University. I think it just goes to the school's T1 line.
Ok - when you were running the livecd, did you have net access?

---

### Post by jdimstrbean on 2006-07-20
No difference with the livecd.  Haven't tried any other distros, but Windows and OSX connect fine as soon as I plug in.

---

### Post by wahman143 on 2006-07-20
> **jdimstrbean said:**
> No difference with the livecd.  Haven't tried any other distros, but Windows and OSX connect fine as soon as I plug in.
If you boot into either, can you post a full IP Configuration?  In windows, it's 'ipconfig /all' from the command line...not sure in MacOS.  Very weird!

---

### Post by jdimstrbean on 2006-07-20
tried typing that into my mate's windows machine, but the command line disappears instantly. I think this is what you want though.

IP Address: 69.176.130.82
Subnet: 255.255.255128
Router: 69.176.130.1

---

### Post by jdimstrbean on 2006-07-20
Here's what I got from the Terminal (OSX not Linux). I don't know if there's anything more in there that would be useful.



```
69-176-130-82:~ Bean$ ifconfig en0
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        inet6 fe80::20a:95ff:feda:4df8%en0 prefixlen 64 scopeid 0x4 
        inet 69.176.130.82 netmask 0xffffff80 broadcast 69.176.130.127
        ether 00:0a:95:da:4d:f8 
        media: autoselect (100baseTX <full-duplex>) status: active
        supported media: none autoselect 10baseT/UTP <half-duplex> 10baseT/UTP <full-duplex> 
10baseT/UTP <full-duplex,hw-loopback> 
100baseTX <half-duplex> 100baseTX <full-duplex> 
100baseTX <full-duplex,hw-loopback> 
1000baseT <full-duplex> 1000baseT <full-duplex,hw-loopback> 
1000baseT <full-duplex,flow-control> 
1000baseT <full-duplex,flow-control,hw-loopback>
```

---

### Post by wahman143 on 2006-07-20
Quite useful actually - for some reason your Ubuntu install is getting a 192 subnet, whereas the output from the MacOS is registering a 69 block.  

Can you post the output of:
```

$ sudo cat /etc/network/interfaces

```

Cheers,
W.

---

### Post by jdimstrbean on 2006-07-20
Here's the output
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

### Post by wahman143 on 2006-07-20
Wow - you have a lot of interfaces there chief :lol:

```

00:14:85:85:23:DE

```
is the MAC that Ubuntu is picking up as Eth0

However,
```

00:0a:95:da:4d:f8

```
is what MacOS is picking up - you have a wlan card?  I think that may be active, and since (unless you bridge) you shouldn't have two cards active at the same time, I think the wlan card is clobbering the ethernet card.

I am unfamiliar with the ubuntu GUI, but I know there is a place in the settings that you can activate/deactivate various cards.  I would start there and make sure that the wlan card is disabled.

Also, if you do a:
```

$ sudo iwconfig

```
that will tell you if you are connecting wirelessly.

HTH,
W.

---

### Post by jdimstrbean on 2006-07-20
okay, eth1 is my wlan card. 

hopefully when I figure out how to disable it (if all else fails, i'll just pull it out), everything will be working fine.

thank you much for you help.

---

### Post by wahman143 on 2006-07-20
No prob!  I'd remove it and reboot the pc...and see what happens.

[https://help.ubuntu.com/ubuntu/desktopguide/C/internet.html](https://help.ubuntu.com/ubuntu/desktopguide/C/internet.html)

I'd check this out - I believe this was the interface I was referring to.

W.

---

### Post by stanz on 2006-07-20
System>Administration>Networking, will show connections & give option to able/disable.
Lil' easier maybe- then pulling the card... ;)

---

### Post by jdimstrbean on 2006-07-21
Removing wlan card worked and Internet was working fine.

That is, until I downloaded system updates. After restart, internet is not working again (can't ping anything). 

Any ideas as to what might have caused this? Is there a way I can rollback updates or should I reinstall(Not a big hassle since it's a fresh install anyway, but I don't want to just experience the same thing again)?

---

