---
title: "[SOLVED] Network-manager for Xubuntu"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by atomic_turtle on 2007-04-20
Hi,

I'd like to make my (technically outdated) Dell Latitude C400 notebook running Xubuntu Dapper into a serious working tool. Part of that is that I've bought a WLAN PCMCIA card that works just fine and I'd like to have a program like network-manager to be able to scan for available wireless networks wherever I happen to be and connect to them. For now, I have configured a permanent connection to my own, WEP-encrypted network here at home by just hacking the details into the /etc/network/interfaces, but that's not the point of it, really...
I know network-manager only with the KDE frontend, knetworkmanager. Can anyone point me to a way of using it on Xubuntu or to a similar program?
Thanks a lot!
Regards,

atomic_turtle

---

### Post by Kobalt on 2007-04-20
You can try to install the *network-manager* & *network-manager-gnome* packages and run them under Xubuntu...

---

### Post by maxamillion on 2007-04-20
You can use the network-manager-gnome along with nm-applet (included in the package) to run in the panel (howto: [here]("http://ubuntuforums.org/showthread.php?t=239178")) or you can try out wifi-radar (also available in the repositories and is considerably lighter on system resources then the network-manager-gnome but it has slightly less features (ie.-no built in WPA support). 

Or if you are adventurous and would like to attempt using something in current development, there are alternatives being worked on such as:
[http://spuriousinterrupt.org/projects/airconfig](http://spuriousinterrupt.org/projects/airconfig)


hope that helped..

---

### Post by atomic_turtle on 2007-04-20
Hi,

thank you very much! I didn't think I would get an answer much faster here than on a Xubuntu-forum - well, there's only an "unofficial" Xubuntu-forum, whatever that means.
I think I'll try wifi-radar first. I don't care much for the WPA support because I want to use it on the go, so I can only connect to unencrypted networks.
Thanks!
Regards,

atomic_turtle

O_O - that brings me back full circle to my Synaptic problem, I can't find the package "wifi-radar".

---

### Post by Tadpole on 2007-04-21
Is there a reason it wasn't included in Xubuntu like it was in K/Ubuntu?

---

### Post by atomic_turtle on 2007-04-22
Hi Tadpole,

good question ;-) It's not there, that's all I can tell you - I didn't remove anything that was there, so I guess it wasn't installed when I upgraded from Breezy to Dapper. 
Regards,

atomic_turtle

---

### Post by atomic_turtle on 2007-04-28
Hi Tadpole [or anybody else],

in the meantime I've installed KDE again. This slows the notebook down quite a bit, especially regarding the time needed to boot, but on the other hand I know [some of] the KDE applications and I kind of know my way around, that's a worthwhile tradeoff to me.
Thus, I have the wlassistant by default which is working. I know that network-manager is better, but the Knetworkmanager is not exactly lightweight and in spite of having KDE, I'd like to keep it as light and fast as possible. I guess wifi-radar is also available for Kubuntu - is it really better than the wlassistant?
Thanks!
Regards,

atomic_turtle

---

