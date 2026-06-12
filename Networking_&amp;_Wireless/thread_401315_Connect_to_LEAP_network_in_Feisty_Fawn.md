---
title: "Connect to LEAP network in Feisty Fawn?"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by mfmbcpman on 2007-04-04
I just installed Feisty Fawn on my laptop and love it. At my school, the network is WPA-Enterprise with TKIP encryption and LEAP authentication. The dialog under Feisty Fawn has no dialog for LEAP, just PEAP, TLS, and TTLS. Thoughts?

---

### Post by chili555 on 2007-04-04
Please check here: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by soro2005 on 2007-04-04
I've just had the same issue, and I finally decided to take a leap (no pun intended) and try [this]("http://ubuntuforums.org/showpost.php?p=2192305&postcount=61") solution here, which, I believe, is for Edgy. Guess what? It works for me on Feisty. Or so I think. At least, I seem to be able to connect with LEAP, although it seems to be taking a couple of attempts every time. So not so sure it's stable. Hope it's not screwing it all up for the future.

---

### Post by theonlyrealperson on 2007-04-19
Does this mean that LEAP support isn't going to be built into (K)Ubuntu's Network Manager in Feisty? Dang. I was looking forward to switching from Ubuntu to Kubuntu, but it looks like I'll have to wait longer.

I have the CVS version of Network-Manager-Gnome which works great, but you can't connect to LEAP in KNetwork-Manager. Also, if you log out of Gnome and into KDE and you are connected to LEAP via CVS Network-Manager-Gnome, KNetwork Manger shuts down. 

I also can get it to work via /etc/Network/interfaces, but even though I've learned to love the Terminal, I prefer the GUI for wireless. Oh well.

---

### Post by RandomUsr on 2007-11-04
I would like to know how you got network-manager-gnome working in the KDE environment. I'm trying to do the exact opposite from Gnome.

I want knetwork-manager which is supposed to work in gnome. It seems that it now has support for the gnome desktop and LEAP. Also, it's supposed to find wireless networks without issue. any help is appreciated.

---

