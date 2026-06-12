---
title: "Atheros 5212 works in Warty but not Hoary?"
date: 2005-09-07
forum: Networking &amp; Wireless
---

### Post by JWL.Freakwitch on 2005-09-07
I've been using Warty on my [Toshiba M35X-S149](http://jwl.freakwitch.net/Linux_Toshiba_M35X-S149.html) for several months. During that install, it had no difficulty getting the included Atheros AR5212 802.11b/g internal modem to work. It used the ath_pci driver by default.

I have a spare partition on the laptop, and I'm finally getting around to upgrading to Hoary, mostly because I really miss KDE and want to give Kubuntu a try. But after installing, I can't seem to get the atheros modem to work automatically.

I've seen the [madwifi howto](http://ubuntuforums.org/showthread.php?t=38972&highlight=atheros+5212) on this forum for the atheros 5212, but before I try it I want to check here .... surely on an updated version of Ubuntu it wouldn't lose functionality? Why would this Just Work(tm) on a previous version, and not on the latest version?

Secondly, why the switch from ath_pci to the madwifi driver?

Thirdly, is it really necessary to compile a module for this? Why would the installation have wifi support without this very common driver/module?

Now, harddata: lspci reveals the wifi modem, but there is nothing about the modem or any drivers in dmesg or iwconfig.

I've been keeping the [Ubuntu Linux on the Toshiba M35X-S149](http://jwl.freakwitch.net/Linux_Toshiba_M35X-S149.html) page for several months now, and want to update it to hoary.

Thanks....

---

### Post by JWL.Freakwitch on 2005-09-07
Found the answer to my own question.

apt-get install linux-restricted-modules-386

modprobe ath_pci

iwconfig

should then list ath0. From there you can simply configure the network from GNOME. 

Cool.

---

