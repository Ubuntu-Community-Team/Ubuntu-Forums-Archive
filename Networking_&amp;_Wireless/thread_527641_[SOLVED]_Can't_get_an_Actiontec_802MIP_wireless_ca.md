---
title: "[SOLVED] Can't get an Actiontec 802MIP wireless card to work"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by tyggna1 on 2007-08-16
I've been trying a number of things to get this wireless card working.  I went out and bought a new one that was listed under a compatibility list--and still can't get that one to work.   The Actiontec is my old card.  I did some research on it a while ago, and it said that it would work with a legacy set of Orinoco drivers.  I don't know how to set up or utilize these drivers--or any set of wireless drivers.  If I can just get one of these cards working, I'll be happy.  I've tried using the windows drivers in Ndiswrapper--but I think I failed to blacklist something.  I'm not sure what blacklisting is either--nor if the actiontec card will work in Ndiswrapper.

In windows, the driver is signed as an IBM high rate wireless combo card--but the physical card says Actiontec 802MIP.  I hope that was enough information.

---

### Post by tyggna1 on 2007-08-17
What is blacklisting and how does it work?

---

### Post by tyggna1 on 2007-08-21
In case you find this post in a search:  Here's what I did to get it working.  

From the terminal I typed:
```

lsmod

```

This gives a list of all the drivers that Ubuntu is currently using.  The Actiontec 802MIP card is based off the orinoco drivers.  If Orinoco_pci and Orinoco aren't listed there, then simply type:

```

sudo modprobe -i orinoco_pci
sudo modprobe -i orinoco

```

That'll install the drivers.

From there, we just need to make sure it's using the right driver--it'll default to prism2* if that is present.  You may either blacklist or remove the prism2 driver--it's your choice

Remove (not the exact coding, replace the * with whatever you found in your lsmod list):
```

sudo modprobe -r prism2*
```


to blacklist:
```

sudo gedit /etc/modprobe.d/blacklist

```

and then type
```

#to make sure linux loads the right drivers for my card
blacklist driver_name

```
somewhere in the blacklist file.

also:  watch out for newer drivers that have been installed, as these could cause problems.  The Orinoco drivers are pretty old.  Here's a list that I had to deal with, and anyone else is free to add to this list by posting:

hostap
prism54

Both these had to be removed/blacklisted

---

### Post by tyggna1 on 2007-08-23
To make this resource more valuable:  This works on my IBM Thinkpad 2662, and the windows drivers had named the card IBM wireless high-rate mini combo card, or something to that effect.  Linux lists this hardware as being named: (command is: sudo lshw -C network)


> 
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 5
       bus info: pci@02:05.0
       logical name: wlan0
       version: 01
       serial: 00:20:e0:8c:1d:71
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=p80211_prism2_pci driverversion=0.2.5 latency=64 link=yes multicast=yes wireless=IEEE 802.11-b
       resources: iomemory:f0000000-f0000fff irq:11


Hope someone finds  this helpful.

---

