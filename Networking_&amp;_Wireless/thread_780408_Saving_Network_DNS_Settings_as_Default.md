---
title: "Saving Network DNS Settings as Default"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by johnnytucats on 2008-05-03
I'm sharing my Mac's wireless connection via ethernet to my PC and finally got it working by adding a couple of DNS servers. I saved the settings as "Home", but when I restart or even after a few minutes I have to open Network each time and re-select "Home" (with the DNS settings) to get things going.

Is there any way to get Network to remember that I want the Home settings when I restart? It's mildly annoying.

I'm on a dual-boot system and Windows XP Home remembers the settings after a restart.



(Hardy Heron 8.04)

---

### Post by prshah on 2008-05-03
> **johnnytucats said:**
> 
Is there any way to get Network to remember that I want the Home settings when I restart? It's mildly annoying.


edit your /etc/dhcp3/dhclient.conf, and look for a line "prepend domain-name-servers ...", if there is a "#" in front of it, remove it, and add the DNS servers you want to the end of the line, separating each by a space.

---

### Post by johnnytucats on 2008-05-03
prshah:

That's got it working...thanks.

Only the first DNS I enter makes it to the Network setting, however. I tried spaces between them, semicolon, semicolon and space. Looks like you have to have a semicolon after the first one or nothing gets added.

---

