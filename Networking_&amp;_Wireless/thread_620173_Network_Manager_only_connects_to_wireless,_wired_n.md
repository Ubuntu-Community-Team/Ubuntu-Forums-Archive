---
title: "Network Manager only connects to wireless, wired network grayed"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by MoRtYMer on 2007-11-22
I tried to found a answer to this but no success yet.

When i have a network cable connected to the laptop, sometimes i have network through wired network and the wired network in the network-manager applet selected, but sometimes the wired network options is grayed and i can only connect to wireless, so when i want to connect to the wired network can't because the option is grayed.

For example i logged to ubuntu, i had the wired network option choosed, then i needed to log on to windows, when i came back to ubuntu the wired network option was "grayed", so i could not choose it, but the cable was still plugged in. And since the wireless network sometimes goes down i need to be connected to wired network.

---

### Post by scrooge_74 on 2007-11-22
go to the network admin and put the wired card in travel mode (sorry forgot the correct term).  Also you can open a terminal and type

sudo ifup eth0 (or the name the system recognizes the card by), if it gives you an error try

sudo ifdown eth0 follow by sudo ifup eth0

---

### Post by MoRtYMer on 2007-11-22
well i've tried doing and i get this:

```
mortymer@mortymer-laptop:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
mortymer@mortymer-laptop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
mortymer@mortymer-laptop:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
mortymer@mortymer-laptop:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.
mortymer@mortymer-laptop:~$ sudo ifdown eth1
ifdown: interface eth1 not configured
mortymer@mortymer-laptop:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.
mortymer@mortymer-laptop:~$
```

---

### Post by scrooge_74 on 2007-11-22
type sudo ifconfig

so you know under what name the system recognizes your cards.

---

### Post by MoRtYMer on 2007-11-22
Well i've got this: 

```
eth0      Link encap:Ethernet  HWaddr 00:17:31:C7:7F:29  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:17:31:BF:1B:78  
          inet addr:192.168.140.130  Bcast:192.168.140.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:febf:1b78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15049 errors:0 dropped:22374 overruns:0 frame:0
          TX packets:3828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4900805 (4.6 MB)  TX bytes:1010443 (986.7 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78698 (76.8 KB)  TX bytes:78698 (76.8 KB)

```

---

### Post by scrooge_74 on 2007-11-22
when you have the wired one plug in you should be able to do 

sudo dhclient eth0  to get an IP

also post your /etc/network/interface

---

### Post by MoRtYMer on 2007-11-23
well this just looks like random behavior, now its connected to the wired network...

Here's my /etc/network/interfaces

```
auto lo
iface lo inet loopback

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

And the ifconfig now that i'm connected by wire

```
eth0      Link encap:Ethernet  HWaddr 00:17:31:C7:7F:29  
          inet addr:192.168.110.53  Bcast:192.168.110.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fec7:7f29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1515 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1325469 (1.2 MB)  TX bytes:325491 (317.8 KB)
          Interrupt:18 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:17:31:BF:1B:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2431 errors:0 dropped:1406 overruns:0 frame:0
          TX packets:143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:244601 (238.8 KB)  TX bytes:6006 (5.8 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Why does this sometimes connects to the wired network and others don't?

---

### Post by MoRtYMer on 2007-11-23
Well i've taken the cable off, and tried to connect to the wireless, after a while of being on the net only with wireless, the wireless has disconnected and there is no wireless network on the list, but the NetworkManager icon is the one when it is trying to connect to a network, the "tag" (when i put the mouse over the icon is "Attempting to join the wireless network '(null)'". When i connect the cable again the wired network option is still grayed so i've used the command "sudo dhclient eth0" and voilá, i've got internet again, but the NetworkManager looks like is on a loop...

I'm getting the sense that the NetworkManager app or the applet still has some big bugs...

---

### Post by scrooge_74 on 2007-11-23
Sure that NetworkManager is still buggy

You can also list your cards in the /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1 
iface eth0 inet dhcp

That helps sometimes.

You can use manual commands (I do it), for example to get unto a wireless network you type:

sudo iwconfig eth1 essid valinor
sudo dhclient eth1

---

