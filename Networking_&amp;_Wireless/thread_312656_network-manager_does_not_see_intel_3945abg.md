---
title: "network-manager does not see intel 3945abg"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by astrand on 2006-12-04
Hi All,

I have a fujitsu 4215 running ubuntu 6.10.  This machine sports an Intel3945 wifi card.  lsmod reports that module ipw3945 is definitely loaded, and I have been able to get it working in System->Administration->Networking with my home network.

My problem is that I would like to use network-manager-gnome to browse open wifi APs and also to enable WPA/PEAP functionality for my university network.

The howtos that I've looked at all say it's simply an 'apt-get install network-manager-gnome' and then click on the network manager icon in the toolbar.  When I do that, I only get a choice for 'wired network', no wifi.

This smells like I'm missing something obvious, but I need some help seeing it.  Any ideas would be greatly appreciated

---

### Post by mcduck on 2006-12-05
You could try removing all configurations for your network interfaces in System/Administration/Networking, and then logging out from Gnome and back again. At least I had some troubles with Network Manager finding my wireless when it was also configured in Network Settings.

---

### Post by sanchrts on 2006-12-05
> **astrand said:**
> This smells like I'm missing something obvious, but I need some help seeing it.  Any ideas would be greatly appreciated

I am afraid that I cannot help answer your question but can only say that I am having the same issue...

I went down the ndiswrapper and blacklist bcm43xx route to get my wireless working - everything seemed to go swimmingly as I can connect to my WPA-protected home network but "Networking" in the gnome System menu does not think my wireless card is configured or working!

You can see from the icons in the notification bar (screenshot below) that I am connected to a wireless network with good signal strength but this is all a mystery to the application that lists my network settings!

[IMG]http://images.fotopic.net/ykrnbg.jpg[/IMG]

---

### Post by Jimmy.Zhou on 2006-12-05
Maybe you can try this:

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/

---

