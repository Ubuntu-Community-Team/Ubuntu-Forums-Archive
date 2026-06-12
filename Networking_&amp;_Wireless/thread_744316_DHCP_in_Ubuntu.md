---
title: "DHCP in Ubuntu"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by rak_freak on 2008-04-03
Hi 

I am having two operating systems on my PC. UBUNTU 7.10 Gusty Gibon and Windows XP. 
I am using a connection of 150kBps . Many times it happens that internet runs in XP but not in UBUNTU.Ubuntu is inable to take IP address . While Windows is able . these situations usally arise when network speed is little less. Any pointers on this ?

---

### Post by lswest on 2008-04-03
during one of those times you can try doing ```
sudo dhclient [name of device]
``` to get an IP address (where name of device=eth0, wlan0, etc.)

---

### Post by rak_freak on 2008-04-03
Hi 

I have tried all of these 

sudo /etc/init.d/networking restart 
sudo ifdown eth0
sudo ifup eth0 

And there are two dhclient3 instances running 

ps -e | grep dhclient3 

2 Entries are shown . 

If the speed becomes good then IP address is picked in UBUNTU. However XP runs at poor speeds as well.

---

### Post by Endwin on 2008-04-03
What kind of network setup do you have? Can you see the logs on your DHCP server? How many Ethernet devices do you have? What is in the file /etc/network/interfaces ?

Helpful if you could post 

```
cat /etc/network/interfaces
```

---

### Post by rak_freak on 2008-04-03
Hi,

 Its a wired network. And I have one ethernet device. It shows one for eth0 and one loopback lo. 

The /etc/network/interface has following kind entry

auto eth0 
iface eth0 something 

As I am in Xp now .. so can't tell exact one :):) 

And where do I see logs of DHCP ?

---

### Post by TheExplorer on 2008-04-03
First make sure you have dhcp configured:

```
sudo gedit /etc/network/interfaces
```Should be:

*auto eth0*[I] 
iface eth0[/I][I] inet dhcp 
[/I]
Mine is eth1 so make sure you have 0 or 1.

Also make sure you have something in your /etc/resolv.conf
Should be your provider's dns nameserver or smth.

Then restart:

```
sudo /etc/init.d/networking restart
```After that I've disabled NetworkManager as it produced the same problems for me as yours.

Stop network manager first:

```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

```Create two files with only the word 'exit' in them. These files are:

[I]/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher
[/I]
Then:

```
sudo update-rc.d NetworkManager remove
```And you can completely remove 'network-manager' and 'network-manager-gnome' via Synaptic.

It helped me a lot. Good luck!

** P.S. The main idea of all this is to configure dhcp manually and remove the buggy Network Manager.**

---

### Post by Endwin on 2008-04-03
What I mean by DHCP server logs is the device that gives you the IP. In most home setups you have something like this

```


INTERNET --- ROUTER/GATEWAY/DHCP --- HOME COMPUTER


```


It is useful to see if your DHCP requests are getting to the router, and if so if the router is responding. So what is it that gives you the IP address something like a linksys router?

What is in your /etc/network interface file is very important for DHCP my setup is like this.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


```

---

### Post by rak_freak on 2008-04-03
Hi 

Everything is same as you have said. I had removed network manager using SYNAPTIC manager. 

The entries in /etc/network./interfaces is also the same. 

Resolv.conf contains entry of 4 DNS Server . 

And for logs .. I will have to restart the System and see :)

---

### Post by TheExplorer on 2008-04-03
Mine is only

*auto eth0*[I]
iface eth0[/I]* inet dhcp*


No loopback as it may also cause troubles. I said I had the same problem as you. Try to remove loopback. You may also need to restart your PC after that.

---

### Post by Iowan on 2008-04-03
The system uses loopback - removing it *may* create more problems than it solves.

---

### Post by rak_freak on 2008-04-04
Hi 

What settings should I have for timeout,retry,reboot  etc parameters in dhclient.conf . So that I can make use of the best, even if the DHCP servers of my ISP are poorly performing .

---

### Post by rak_freak on 2008-04-04
Finally succeded in running the internet at UBUNTU. The method I adopted is , ran the love CD of UBUNTU and copied all the settings files viz. dhclient.conf, resolv.conf, interfaces to my installation
What I have figured out is that , interfaces had an entry like this 
auto lo
iface lo inet [COLOR="DarkOrange"]dhcp[/COLOR] 

It should have been 
iface lo inet [COLOR="DarkOrange"]loopback[/COLOR] 

Working fine now. :):)

---

### Post by TheExplorer on 2008-04-05
Well I removed it intentionally and it works like a charm for me.

---

