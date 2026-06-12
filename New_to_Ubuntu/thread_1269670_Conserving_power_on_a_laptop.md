---
title: "Conserving power on a laptop"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by kiwizoid on 2009-09-18
Hi guys, I've been using Jaunty Ubuntu for a few months and I'm loving it, apart from the little problem of a shorter battery life than in Windows. I downloaded PowerTOP and I enabled all of the suggested actions given so far, and I've been watching the terminal window for a bit and I've noticed that eth0 is using the most interrupts. At first I thought it was my wireless card, until I turned off the card and noticed that eth1 went away, so I've assumed/inferred that eth1 is my wireless card.

So this leads me to a few questions: 

1) How do I figure out what eth0 actually is? I think eth0 would be my ethernet adapter, but I don't have an ethernet cord ever plugged in while I'm in class, so it doesn't make sense, but then I don't know what else it would be.

2) How would I disable eth0, if it ends up being something that sounds unnecessary?

3) Is there anything else I could do to conserve power that isn't automatically done by PowerTOP, apart from turning down the brightness and limiting the number of programs I have running?

Thanks in advance, and sorry in advance if this is too many questions :)

---

### Post by Sealbhach on 2009-09-18
eth0 would be your ethernet connection, so you would need it.

Run

```
lshw -C network
```

Look for the "logical name" eth0. It will tell you what it is. Your wireless card would have the name "wlan0" or something similar.

You could try the command "killall eth0" and see what that does, it will kill that process for your session.

.

---

### Post by kiwizoid on 2009-09-18
Thanks for the reply :) Here's what lshw -C network printed that seemed relevant:

```
[B]description: Ethernet interface
       **product: MCP67 Ethernet**[/B]
       **logical name: eth0**
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII

  *-network
       [B]description: Wireless interface
       product: BCM4312 802.11b/g[/B]
       **logical name: eth1**
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=10.134.222.245 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
```"killall eth0" responded with no processes killed, so I wasn't able to test disabling eth0 for a session. Does the wireless interface still need the ethernet interface in order to function? Given the names, I'm guessing/assuming they're both interfaces to interact with the network card, but at the same time the high interrupts for eth0 make me think it goes eth1 -> eth0 -> network card. Or I could have it totally wrong... my understanding of hardware is a bit sketchy :)

---

### Post by bigboy7foru on 2009-09-18
from what i understand eth0 is always needed

---

### Post by kiwizoid on 2009-09-18
Ah, okay... that's too bad. Thanks for all of the help anyway. :)

---

### Post by shae on 2009-09-19
If you can, I would suggest you undervolt your laptop!  [http://www.linux-phc.org/forum/viewtopic.php?f=13&t=67](http://www.linux-phc.org/forum/viewtopic.php?f=13&t=67)

---

### Post by mikewhatever on 2009-09-19
There are some tips for dealing with ethernet here [http://lesswatts.org/tips/ethernet.php](http://lesswatts.org/tips/ethernet.php). You can also try disabling the interface with: sudo ifconfig eth0 down

**sudo ifconfig eth0 up**      to bring it back up

---

### Post by talsemgeest on 2009-09-19
The best thing I ever did to conserve power on my laptop was switch to Xubuntu. It is considerably lighter on system resources that Ubuntu and, as such, uses quite a lot less power. If you really want to squeeze every last drop out of your battery, I would definitely suggest Xubuntu.

---

### Post by kiwizoid on 2009-09-19
Thanks for all of the replies :) I was able to disable eth0 with no noticeable consequences, so that should help power consumption to some degree. I tried some of the suggestions on lesswatts.org but couldn't put any of them to use, because my wireless card refuses to give data (or none is available) even as superuser.

I think compiling a new kernel is a bit out of my league at this point, but I'll keep the link in mind once I feel a bit more confident to try it. Would switching to Xubuntu be like installing an update or would it be like a totally fresh install of a new OS where I'd have to back up my data?

---

### Post by mike555 on 2009-09-19
You might want to read about "WattOS" , it's a lighter version , but not quite as nice .....    [http://www.planetwatt.com/](http://www.planetwatt.com/)

---

### Post by halitech on 2009-09-19
> **kiwizoid said:**
> Thanks for all of the replies :) I was able to disable eth0 with no noticeable consequences, so that should help power consumption to some degree. I tried some of the suggestions on lesswatts.org but couldn't put any of them to use, because my wireless card refuses to give data (or none is available) even as superuser.

I think compiling a new kernel is a bit out of my league at this point, but I'll keep the link in mind once I feel a bit more confident to try it. Would switching to Xubuntu be like installing an update or would it be like a totally fresh install of a new OS where I'd have to back up my data?

If you are already running 9.04, you should be able to open a terminal and run
```
sudo apt-get install xubuntu-desktop
```
if you want it lighter, run
```
sudo apt-get install xfce
```
if you want even lighter, try LXDE
```
sudo apt-get install lxde
```

Basically, the main parts of (K)(X)Ubuntu are the same, the desktop environments just change the default apps that are installed with each one. Xubuntu used to be very light but the recent versions aren't much lighter then Ubuntu anymore.

---

### Post by shae on 2009-09-19
> **kiwizoid said:**
> Thanks for all of the replies :) I was able to disable eth0 with no noticeable consequences, so that should help power consumption to some degree. I tried some of the suggestions on lesswatts.org but couldn't put any of them to use, because my wireless card refuses to give data (or none is available) even as superuser.

I think compiling a new kernel is a bit out of my league at this point, but I'll keep the link in mind once I feel a bit more confident to try it. Would switching to Xubuntu be like installing an update or would it be like a totally fresh install of a new OS where I'd have to back up my data?

I believe the Linux-PHC people have a PPA with an already patched kernel.

---

