---
title: "network works only if i boot with cable plugged"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by Rikiji on 2007-10-06
I installed gutsy beta on my laptop featuring "Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)".

When i boot the system with an ethernet cable plugged i can connect to the network,both via cable and wireless, just switching through gnome network manager.

If i boot without the ethernet cable plugged there's no way i can connect, not even after "sudo /etc/init.d/networking restart".

What should i do to resolve this annoying problem? :confused:

---

### Post by megamania on 2007-10-06
Have you tried checking the file /etc/network/interfaces?

I'm not an expert, but that would be a good place to start.

---

