---
title: "Setting up a Wireless Connection"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by orrymr on 2011-03-18
Hi guys, 
I've just installed Meerkat (I'm dualbooting with Windows 7), and am having some issues getting my wireless internet working. I'm not exactly sure what steps are meant to be taken to get it working, but I've tried to add a new wireless network. I then type in the SSID (which I assume is NETGEAR, since this is my router?). I type in my mac address... and then...? Is it meant to work from there? Not at all sure - any help would be much appreciated.
Thanks in advance.

---

### Post by tkelito on 2011-03-18
First step is going to be knowing your network name and password.  It may or may not be 'Netgear' unless you left the default settings on your router, which I do not suggest.

If your network card is being detected correctly you should by default see it along the top bar (to the right) and it should show you a list of network connections if you click on it.  From there it should be finding your network name (also referred to as the SSID) and connecting to it.  If you have encryption it should then prompt you for a password.

Unless you are connecting to a hidden network or doing something advanced at no point should you need to manually type a network name.  I can only think a few cases where I would ever need to type out the MAC Address.

Any more detail you can give us?

---

### Post by orrymr on 2011-03-18
I'm not sure that my network card is being picked up (refer to attached .png)

---

### Post by Mr.Dee on 2011-03-18
What type of network card do you have?  Some network cards will work like a charm and some you might need to find a driver for.

---

### Post by josephmills on 2011-03-18
what happenes if you type in 
```

ifconfig 

```
In the terminal Do you see a wlan0 or do you just see eth0 and lo? Also have you updated and upgraded?
```

sudo apt-get upgrade

```
```

sudo apt-get update

```
Also could you go to the teramanial and type in 
```

lspci -vnn | grep 14e4

```
ok thanks

---

### Post by Bob Abouille on 2011-03-18
Did you install Ubuntu 10.10 with a LAN line inserted? It will setup your wifi card, but you have to be connected and check "search for updates"

I was told 100 different things and this i discovered on my own.

---

### Post by walt.smith1960 on 2011-03-18
> **orrymr said:**
> I'm not sure that my network card is being picked up (refer to attached .png)

what happens if you left click or right click the icon that is several arcs and the red exclamation point?  If there weren't *some* sort of network adapter recognized, I don't think you'd have the red exclamation point, it'd be grayed out.  

If this isn't helpful, can you plug into a router with a cable?  If you can do that and there's a connection established (two arrows, one pointing up one pointing down) then click system-administration-additional drivers.  Is there a network adapter listed? If so, click 'activate' and restart if necessary.  If you do the cable routine, you'll need to restart after plugging in the cable for the connection to be recognized, I'm pretty sure.

---

### Post by orrymr on 2011-03-19
@Mr.Dee -> Netgear wg311v3
@Joseph -> done, done, and refer to attachment. Capabilities: <access denied> -> Why is that?
@Bob -> I installed it with everything disconnected. 

From my room I'm only able to connect via wireless; I've got no ethernet cable. I only see eth0, no wlan0

---

### Post by orrymr on 2011-03-19
When I did <some command, can't remember which> I eventually saw:
*- network UNCLAIMED, which means that no driver has claimed the device (don't know why I don't try the obvious things first...). Anyway, having some problems at the moment with ndiswrapper, but hopefully it should be sorted soon.

Thanks for the help!

---

