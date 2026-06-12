---
title: "Can't connect to wireless..."
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by Acheront on 2007-01-08
I've read countless number of guides about setting Ubuntu to work with wireless connections but none work on my laptop >__>

I go to configure my Network Connection. Under Wireless connection's properties it says the Interace name is eth1. I am able to find all the wireless networks in range, including my neighbour's. I select mine, enter the WEP key and everything and click OK.

I then get out of Network Settings, but it won't connect to my wireless network. I double-click on my Network Connections icon, and it claims the status is 'Disconnected'. I cannot figure a way to connect it.

Some guides mention something about wlan0, but my computer cannot find that. However, I assume its eth1 since my network *can* be found under it.

Can anyone help please?

---

### Post by scrooge_74 on 2007-01-09
This is like DejaVu, someone had the same problem earlier today.

[http://www.ubuntuforums.org/showthread.php?t=333731](http://www.ubuntuforums.org/showthread.php?t=333731)

Also check 
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by Acheront on 2007-01-09
Still doesn't help...

My Ubuntu seems very dodged up. I try to install network-manager-gnome in the Terminal, but it always says that the package is not found.

I go to Synaptic Package Manager and try to search for network-manager, but it cannot be found. At the bottom, it says 1063 packages listed, 1063 installed, 0 broken, 0 to install/prade, 0 to remove, meaning my computer doesn't even have network-manager-gnome, or other uninstalled packages at all. o_O


I installed Ubuntu 6.06 with the Live CD.

---

### Post by scrooge_74 on 2007-01-09
maybe you need to enable the other repositories

---

### Post by Acheront on 2007-01-09
Can you please explain 'enabling other repositories' since I am quite new to Ubuntu.

My Ubuntu laptop has NO CONNECTION to the internet at the moment since it won't connect to the wireless network that other XP and Vista computers in the house are connected to.

---

### Post by scrooge_74 on 2007-01-09
Synaptic has an option to enable other download servers.  Ubuntu comes with default option to only use the repositories Ubuntu supports, but there are thousand of other programs in the rest of the Debian repositories.

You just need to enable them.

I did a quick search and ther is a network-manager package supporte for ubuntu in synaptic.

Did you try lowering your security to see if you can connect, that sometimes is a problem at the begining, just tell your router not to use the WEP key for a moment until you can figure out what is wrong.

Also check that the WEP key you are entering is in ASCII or in HEX, you may have the router on one and the laptop in another.

---

