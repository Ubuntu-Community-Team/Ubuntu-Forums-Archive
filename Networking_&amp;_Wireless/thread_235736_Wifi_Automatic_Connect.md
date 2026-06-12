---
title: "Wifi Automatic Connect?"
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by Mr. Picklesworth on 2006-08-13
I am looking for a utility that will automatically scan for and connect to wireless APs, or at least, when disconnected from an AP, attempt to reconnect.
(Ubuntu occasionally just loses its connection and makes no attempt to reconnect, which is a bit of a pain if I'm doing any long-term stuff over the network).

I found this, which looked promising:
[http://www.ubuntuforums.org/showthread.php?t=18466](http://www.ubuntuforums.org/showthread.php?t=18466)
But, judging by page 15, it is not working very well anymore :(

Do you have any suggestions?

---

### Post by mscman on 2006-08-13
[NetworkManager]("http://www.gnome.org/projects/NetworkManager/") is a good choice, one that I use on my laptop. It's pretty straightforward and easy to use.

Also, there is a great HowTo at UDSF about NetworkManager and WPA support:
[http://doc.gwos.org/index.php/Network_Manager_with_WPA](http://doc.gwos.org/index.php/Network_Manager_with_WPA)

Hope this helps!:D

---

### Post by Mr. Picklesworth on 2006-08-13
Okay, found it in Synaptic as network-manager and network-manager-gnome.
Yay!

I'll install it and play around once CVS here finishes with its thing.


Edit:
Okay, I've installed it, but I can't find this panel applet that is mentioned n the description and nothing has appeared in any menus.
Through the terminal I can find NetworkManager, but no GNOME interfaces.

---

### Post by mariner09 on 2006-08-13
nm-applet will launch the applet.  It should appear in the notification area.

---

### Post by Mr. Picklesworth on 2006-08-14
Hm... it doesn't seem to like my wireless card?

When it starts, it is only allowing for wired connections and it makes no mention of wireless.
(While at the same time my wireless network is working fine using the default network manager).

I'm using an Asus WL-138g WLan card, which uses mrv8k51 (Marvel) drivers.
It is not listed [here.](http://live.gnome.org/NetworkManagerHardware)
Does that mean it won't work? (If so, seems a bit strange).

---

### Post by Mr. Picklesworth on 2006-08-16
So, is there some way to get NetworkManager to support my WLan card?
The card supports scanning, and it works fine through ndiswrapper.

Perhaps there's a file to edit, or it has to be recompiled?

If not, It seems that I'll unfortunately need a different program...

---

