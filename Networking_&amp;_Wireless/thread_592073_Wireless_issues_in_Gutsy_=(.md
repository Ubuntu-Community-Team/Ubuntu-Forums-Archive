---
title: "Wireless issues in Gutsy =("
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by Maelgwyn on 2007-10-26
Hey guys - I previously had wireless running in Edgy by using the script found [here]("http://www.linux.net.nz/pipermail/aucklug/2007-August/001991.html"), but when I rebooted into Gutsy after upgrading via update-manager -d, my wireless no longer works! I've since plugged in a network cable so I at least *can* use the internet, but I'd love to go wireless again!

My current /etc/network/interfaces reads as:
```
auto lo
iface lo inet loopback


#iface eth0 inet dhcp

 
iface eth0 inet dhcp





auto eth0
```

Any ideas as to how I can get the wireless working? We're on a WPA-Pre Shared Key with TKIP if that's of any help...

---

### Post by conjur3r on 2007-10-26
Have you tried using the gnome network manager which comes with Gutsy?  It's a GUI app which lets you configure wired and wireless networks.  You shouldn't need to edit configuration files anymore.

If you're having issues with WPA encryption with a hidden SSID, then try using another tool called wicd.

---

### Post by Maelgwyn on 2007-10-26
Yeah I've tried the GUI tools.... Still isn't working =(

---

### Post by conjur3r on 2007-10-26
Try the wicd tool.  Gnome Network Manager went backwards since Feisty and unfortunately, is still poor in Gutsy.  It will not let me connect to my WPA-PSK encrypted router with a hidden SSID.  Wicd does.

Also, you mentioned that you upgraded from Edgy to Gutsy?  I thought the only way to upgrade to Gutsy was from Feisty?

---

### Post by Maelgwyn on 2007-10-28
I meant Feisty.... *blush*

And where do I find wicd? It's not in apt-get =(

---

### Post by rcatman on 2007-10-28
I abandoned network-manager in Feisty when I needed to go wireless. I found wicd works great. 

The download page is:
[https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460]("https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460")

The latest release is wicd 1.3.1. Download wicd_1.3.1-all.deb to your desktop and install. 

The wicd homepage is [http://wicd.sourceforge.com/](http://wicd.sourceforge.com/)

enjoy :)

---

