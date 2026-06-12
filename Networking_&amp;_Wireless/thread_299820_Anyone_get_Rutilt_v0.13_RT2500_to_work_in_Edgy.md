---
title: "Anyone get Rutilt v0.13 RT2500 to work in Edgy?"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by videodrome on 2006-11-14
Has anyone managed to get the Rutilt wireless network manager software v0.13 to work under Edgy? It is for Ralink chipset wireless cards.

Not the version in Synaptic, which is older, but the current and newest version available here: [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/)

After running ./configure.sh and make, make install or checkinstall throw errors. And once you start the program, clicking "scan" errors out big time after you enter both the sudo and or root password. This happens even if you run the configure script with the prefix=nopassword flag.

I tried changing the shebang to fix path errors, installing it all as root, etc... no luck.

Note that I do not want to start the program with sudo, even if that seems to bandaid the problem. 

Thanks

---

### Post by ninjaPants on 2006-11-30
What errors are displayed when you run make install? 

I just set this program (v0.13)up yesterday and it installed fine. I'm using gksudo to open it. I know it can be dangerous to run a program as su, but I'll take my chances until there's a fix released. I guess this isn't much use to you if you don't want to run the program as root. I'm guessing it asks for your root pw because it's effectively changing settings in system>administration>networking and that can't be done by a normal user. I saw a post on the rt2500 board that looked like this one and suggested rolling back to v0.12. 

Wow. I don't think I was helpful at all, but if you find a real fix to this let me know.

---

