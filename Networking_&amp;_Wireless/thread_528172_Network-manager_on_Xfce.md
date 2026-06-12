---
title: "Network-manager on Xfce"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by atomic_turtle on 2007-08-17
Hi,

can anybody help me in setting up the network-manager on my Xubuntu subnotebook? I have already installed the packets network-manager and network-manager-gnome. Now, according to the UU Wiki, when I just add the # to the interfaces I want it to manage in the /etc/network/interfaces, it should work, there should automatically be a network-manager icon in the panel - at least on Gnome. The Wiki doesn't say anything about Xfce and it obviously doesn't work quite like that on Xfce. I have no icon and I couldn't yet even find the network-manager in my X menu. Also, I can't find this roaming mode in the properties of any of my network devices.
Thanks a lot!
Regards,

atomic_turtle.

P.S.: Okay - after some trying, when I comment or delete the contents of the /etc/network/interfaces, it says "roaming mode enabled" when I look in the network settings. However, there's no icon for the network-manager and no menu point and the notebook doesn't detect my home wireless network which isn't a problem with the alternative method.

---

### Post by mrbungle on 2007-08-28
im having the same problem, anyone have some ideas?

thanks

---

### Post by atomic_turtle on 2007-08-29
Hi mrbungle,

I've thrown out network-manager in favor of wifi-radar and so far, that seems to work fine. 
I've only tried it out once, but it seems fine, even when I leave the logon data for my own wifi-network here in the house in the /etc/network/interfaces so the notebook will automatically log on to this network whenever I'm home and I can still search for and connect to other networks when I'm on the go. 
Regards,

 atomic_turtle

---

