---
title: "network-manager-gnome does not see my wireless card"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by PPower on 2006-07-17
For some reason my wireless card on the bcm43xx driver does not show in network-manager-gnome, only my wired one which is disabled cause i have no cable.

How do i get network-manager-gnome to see my card?

---

### Post by tturrisi on 2006-07-17
[http://www.ubuntuforums.org/search.php?searchid=6809788](http://www.ubuntuforums.org/search.php?searchid=6809788)

---

### Post by PPower on 2006-07-17
That search didnt answer anything. I could not find the answer

---

### Post by tturrisi on 2006-07-17
Does the card work at all manually configuring it?  Do a search for bcm43xx, there's 200+ threads about it.   here'sone: [http://www.ubuntuforums.org/showthread.php?t=197102&highlight=bcm43xx](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=bcm43xx)

---

### Post by PPower on 2006-07-17
Yeah. Even network-manager works, its just the applet does not have my wireless card in the list

---

### Post by tturrisi on 2006-07-17
can you use network admin to config the connection?  system > administration  > networking

---

### Post by PPower on 2006-07-18
You are not getting the point here.

The network works fine. I set it up with network admin and a little help from the commandline to set the AP. Network-manager works cause it makes it so I dont have to set the AP every bootup. Just network-manager-gnome does not see my card in its list.

It may be the fact I have a disabled eth0 before the wireless eth1 and network-manager-gnome just borks out.

---

### Post by Krzysztof on 2006-07-18
> **PPower said:**
> You are not getting the point here.

The network works fine. I set it up with network admin and a little help from the commandline to set the AP. Network-manager works cause it makes it so I dont have to set the AP every bootup. Just network-manager-gnome does not see my card in its list.

It may be the fact I have a disabled eth0 before the wireless eth1 and network-manager-gnome just borks out.


There is a little problem naming two tools. One is network-settings (System/Administration in gnome menu), which displays network adapters and lets to configure them. While the second one is NetworkManager which comes with nm-applet (in gnome) to configure the connections. Which one do you mention? If you have a connection set up and working and you cannot see the wi-fi adapter in the list of nm-applet network interfaces, then it means that you just want NetworkManager to configure changing wifi networks. If I am correct then you should comment out yout wifi card in /etc/network/interfaces. Otherwise NetworkManager will not see it at all. 
I had this problem for a long time.

---

### Post by tturrisi on 2006-07-18
> There is a little problem naming two tools. One is network-settings (System/Administration in gnome menu), which displays network adapters and lets to configure them. While the second one is NetworkManager which comes with nm-applet (in gnome) to configure the connections. Which one do you mention? If you have a connection set up and working and you cannot see the wi-fi adapter in the list of nm-applet network interfaces, then it means that you just want NetworkManager to configure changing wifi networks. If I am correct then you should comment out yout wifi card in /etc/network/interfaces. Otherwise NetworkManager will not see it at all.
I had this problem for a long time.

There's one basic networking tool that comes w/ a default Ubuntu Gnome install, the executable is called network-admin.  There is an applet that can be added to the panel called network monitor.  But network monitor is just an icon that graphically shows network activity and it's "properties" link to network-admin.

There is another utility called network-manager that can be installed via Synaptic.  And there is a front end (gui) to network-manager called network-manager-gnome.

These are 2 separate & distinc different network utilities, the network-admin & network-manager.

> You are not getting the point here.

The network works fine. I set it up with network admin and a little help from the commandline to set the AP. Network-manager works cause it makes it so I dont have to set the AP every bootup. Just network-manager-gnome does not see my card in its list.

It may be the fact I have a disabled eth0 before the wireless eth1 and network-manager-gnome just borks out.
I understand you now.  I no longer use network-manager-gnome, however, when I did use it what I did was first use network-admin to disable the device.  Then I used network-manager-gnome or wifi-radar to configure my connections.  Now I just use network-admin & try to keep things as simple as possible anymore.

I originally used net-manager or wifi-radar so I could connect w/ WEP, as I had trouble getting net-admin to use WEP.  I got WEP to work in net-admin by putting a hyphen after every 4 characters like so:
1234-5678-90

Have you found any other threads here re net-manager-gnome and the broadcom driver?

---

