---
title: "bridge-utils / internet connection sharing"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by rubberglove on 2007-03-29
Hi all:

I am trying to set up my ubuntu box (just upgraded to feisty, amd_64) as a bridge. 
I have two ethernet cards installed in the computer, eth0 connects to my router, and eth1 connects to another computer (a powerbook). 

I'd like to be able to share the network connection from the router as transparently as possible (I'd prefer if the powerbook had a more or less 'direct' path to the router, to make my life easier in terms of port forwarding and all that). Why am I doing this? Well, I'd like to:

-maintain a gigabit connection between the two computers (for filesharing and because I tend to use XDMCP from the powerbook to the desktop) 

-avoid using wireless when the powerbook is sitting in its usual spot (it works okay... but is a tad slow for XDMCP)

-avoid running any more ethernet cables across the room

-avoid buying a gigabit switch/router

I've tried using bridge-utils, but can't quite get it to work. 

here are the commands I'm trying to use:

```
ifconfig eth0 0.0.0.0 up
ifconfig eth1 0.0.0.0 up
brctl addbr br0
brctl setfd br0 0
brctl addif br0 eth0
brctl addif br0 eth1 
dhclient br0
dhclient eth1
```

confusingly enough, these commands worked one time, but since then (after a reboot) I have not been able to get it working. That is, the internet connection on the desktop works fine, but I cannot get an IP through DHCP on the powerbook. Setting the IP manually on the laptop lets me ping the desktop, but not the router or anything else. 


any help would be appreciated.

thanks.

---

### Post by dalziel_86 on 2007-03-30
You need to bring up the bridge with something like
```
ifconfig br0 up
```

or if you want a more advanced setup:

```
ifconfig br0 192.168.100.5 netmask 255.255.255.0 up
```

I'm having some trouble with bridging myself at the moment. I'm able to bridge the connections, but then the machine doing the bridging loses access to the Internet. So I can't say this will definitely solve your problem. :)

---

### Post by confuciusquinn on 2007-11-23
Do you know if you need a different kind of ethernet cable that connects the two computers? somethin to do with patch and crossover? With the computer that the internet is getting bridged to its not even showing any cable is connected at all (its a windows box)

---

### Post by confuciusquinn on 2007-11-26
bump?

---

### Post by vaalbygaardsvej on 2007-12-07
yeah, you need a crossed cable between the two computers when you din't youse a hub/switch

but wheather or not you will achieve 1GBit connection between the computers im not sure.

---

### Post by confuciusquinn on 2007-12-07
Ah.. I think all i have is patch cables, unfortunately. The cables that you normally get with routers and such are called 'patch' cables correct?

---

### Post by vaalbygaardsvej on 2007-12-07
dunno sorry. but if the nic's don't even show connection then theres you problem. im having similary problem on my box. i have a linksys with 4 ports. and i want it to act like a switch. but then i also need crossed cables.

---

### Post by Het Irv on 2007-12-08
Yes, patch cables come with switch/routers.

---

