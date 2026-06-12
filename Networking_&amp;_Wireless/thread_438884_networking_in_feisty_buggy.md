---
title: "networking in feisty buggy"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by eewald on 2007-05-10
networking in feisty is buggy as ***, i have never seen anything so bad before. 

my computer at work is behind a static ip server, not dhcp server. so the ip address and domain name must be specified manually. 

but connection is really, i mean REALLY unstable. firefox (and opera) regularly drop connection for 2 to 10 minutes, doing it at least once in an hour. msn and jabber connections, evolution's connection to exchange server and even internet radio work (almost) seamlessly same time. on the other hand - ping brings no responses and apt-get can-t connect to repos. mac and windows machines nearby work perfectly fine... 

i uninstalled network-manager, but no help. what can i do? 

(i do not know if these things are related, but there is a dhcp server too in office building used by another company and if network is not configured manually, my computer automatically goes to another company's network)

---

### Post by dca on 2007-05-10
I copied all my files to my server and downgraded to  606LTS (Dapper).  After install, added network applet (the one available in the add to panel options) to top bar and installed WiFi Radar.  Moved WifiRadar launcher from menus to top bar next to network applet...  
 
This network manager dealie has had problems on all distro(s), RedHat/CentOS being the worst because it acknowledges network but drops constantly and reconnects a couple seconds later...

---

### Post by Tarrasque on 2007-05-10
I set up my first WiFi network yesterday on Ubuntu 7.04

I'm using a NETGEAR WG111v2 USB dongle (which, by the way, seem to be working flawlessly and allowed me to connect to the WiFi LAN as soon as i plugged it in).

I'm basically zero knowledge on networking, but I have been able to set up the connection  by unchecking the "roaming" checkbox on the network manager thing (I believe it's the applet on the top right of the upper bar, isn't it?) specifying the ESSID name, WEP key and things, so I don't think there is any error on my side.

Still, internet navigazion is horrendously slow. By monitoring the network traffic I see there are some "peaks" of activity, where traffic goes over 10 kb/sec, and long periods of inactivity.

This makes application installing through synaptic utterly impossible, because I invariablily time out.

I'm sure it's not a general problem, because by connecting direcly via wired connection to the router I had no problem. Nor is a distance from the access point, because I have a Windows laptop even farther from it working wlawlessly.

So, I guessed if my problems could be related to the ones you're experiencing and how can I solve them.

Do I have to uninstall something? What's that "network-manager" you're talking of? And that "WiFi radar".

I wouldn't like to downgrade to a previous version of Ubuntu, if it's possible...

---

### Post by eewald on 2007-05-11
so basically there is nothing i can do but change to distro that does NOT use network manager? 

can anybody recommend one?

---

### Post by wieman01 on 2007-05-11
> **eewald said:**
> so basically there is nothing i can do but change to distro that does NOT use network manager? 

can anybody recommend one?
What a sad state of affairs... Let's hope the next version of Ubuntu will fix it. Why don't you try Wifi-Radar? From what I have learned so far, it is fairly reliable and support static ip as well as DHCP.

---

### Post by eewald on 2007-05-11
thanks, i'll try that wifi-radar. changing a distro would be an annoyance i would preferably avoid.

---

