---
title: "Network IP's only available after /etc/init.d/networking restart"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by wild_oscar on 2008-04-24
Currently in Hardy with my laptop, with the 2200BG wireless card:
```
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth1
       version: 05
       serial: 00:15:00:3c:ad:96
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.111 latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g

```

Running wireless with roaming mode enabled. It connects to the internet without a problem, BUT:

I cannot ping/ssh/access my local network's computers, unless I run 

```
/etc/init.d/networking restart

```

After this I can ping computers until I touch Gnome's network manager (nm-applet 0.6.6).

If, for example, I click the icon and re-choose the same wireless connection I am connected to, ping will result in
```
From 192.168.1.106 icmp_seq=8 Destination Host Unreachable

```

If, once again, I restart networking with the init script, it will start working again.

I have my router's IP as default gw in route -n.


Anyone got a clue why this happens?

---

### Post by kamazu on 2008-04-24
Hi,

can you post the output of 

```
ip route
```

before and after touching nm applet...

---

### Post by wild_oscar on 2008-04-24
Before:

```
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.111 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.106 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth1 
default via 192.168.1.1 dev eth0  metric 100 
```

After:
```
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.106 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0  metric 100 

```

---

### Post by ashughes on 2008-04-24
I see the same issue when running straight off the live CD.

I am going to try installing and see if that matters.

---

### Post by ashughes on 2008-04-24
PS.  If worse comes to worse, I suppose I can always set it up so /etc/init.d/networking restart runs at startup

---

### Post by wild_oscar on 2008-04-25
So, basically, if I click on one of the wireless networks, the removal of 
```
default via 192.168.1.1 dev eth1 
```

makes my default gw disappear. Any idea why?

---

### Post by wild_oscar on 2008-04-25
Thinks work normally if eth0 (wired) is changed to DHCP instead of "static IP".

As a result, I submitted a bug in [http://bugzilla.gnome.org/show_bug.cgi?id=529865]("http://bugzilla.gnome.org/show_bug.cgi?id=529865")

---

### Post by ashughes on 2008-04-25
Now that I have installed hardy, I don't have to run /etc/init.d/networking restart but I do have to manually select a wireless network.  I cannot seem to set one as default.

---

### Post by kamazu on 2008-04-25
So, how I understand it you have two network interfaces.
The wireless is eth1 and provides the network connection. After starting /etc/init.d/networking the device eth1 is brought up and set as the standard gateway and everything is working fine.
Touching the applet changes this and removes the device as well as the standard gateway. Why it does so, I don't know. eth0 is left and has no connection to the net...
The script in /etc/init.d/networking is reading the configuration file /etc/network/interfaces. Can you post the output of 
```
cat /etc/network/interfaces
```
and 
```
ifconfig -a
```

I uninstalled the applet in my desktop-machine, but this might not be practical on your machine (laptop?). Does someone know where the applet stores its information and what could cause it to interfere with /etc/network/interfaces?

greetings 

kamazu

---

### Post by humina on 2008-10-17
I also have the same problem.  I have been reluctant to implement a user script to run the restart command on boot because my computer should grab the info properly on boot.  I've pretty much given up and decided to copy/paste a restart script that someone else wrote because the problem is not getting fixed.  Bummer.

---

