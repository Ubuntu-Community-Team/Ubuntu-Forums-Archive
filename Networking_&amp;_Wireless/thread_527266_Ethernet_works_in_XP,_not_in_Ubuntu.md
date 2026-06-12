---
title: "Ethernet works in XP, not in Ubuntu"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by AbsolutMayhem on 2007-08-16
Yesterday, I installed ubuntu as a second os on my kids' old desktop computer. It seemed to install ok, but did not go through the update process after installation. I don't think the ethernet card is messed up, because I can connect with it via Win XP. I also checked the ethernet cord itself by connecting that to my son's ubuntu laptop and it worked fine. 

Since my son's laptop internet connection worked, I entered the DNS settings from the laptop to the desktop. Even after doing this, I couldn't ping, or access the internet. Of course, I can't access synaptic the desktop either.

Maybe the ethernet card is incompatible with Ubuntu? It's a linksys LNE100TX ethernet adapter (LNE100TX v4). But ubuntu seems to detect it ok, and it is activated in network settings. There is no wireless card in the desktop, ethernet card is internal, modem is deactivated, and set to DHCP.  I use DSL, and a linksys router. All other ubuntu machines in the household connect via ethernet with no problems, and no special setup procedures. (I can't seem to get the wireless working, but that's a separate issue :(). What am I doing wrong?

I followed new2this' instructions in the "ethernet card works randomly" post, but still can't connect.

---

### Post by scrooge_74 on 2007-08-16
Try this, reboot your router.  It could be that the router sees the card in another machine, when you boot to ubuntu it says it is something else.

Also check how is recognize by the system from a terminal type ifconfig

Another idea is to set the card as (on the road sorry dont remember the english term)

and then let network-manager try to configure the conection

---

### Post by AbsolutMayhem on 2007-08-16
Scrooge- Thanks for the suggestion. I rebooted both the modem and the router and now it works. Woohoo! ;-D

---

