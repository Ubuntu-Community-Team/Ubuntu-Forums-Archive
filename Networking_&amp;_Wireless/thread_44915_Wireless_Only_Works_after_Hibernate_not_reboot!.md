---
title: "Wireless Only Works after Hibernate not reboot!"
date: 2005-06-28
forum: Networking &amp; Wireless
---

### Post by sadza on 2005-06-28
Hey all; I've just installed Hoary on my laptop. Everything went great, automatically recognised my cisco mini pci wireless card. This is the first time I've actually installed and plan to use linux as a replacement to windows, I have fooled around with many other distro's like Gentoo, slack and Red Hat, but Ubuntu is the easiest to use. 

Anyway onto the problem: After installing a wireless app for gnome panel, my wireless card will only log onto networks after I come out of hibernation. If I turn my laptop off or reboot, the wireless card is recognised but it will not do anything. I have tried with iwconfig as this is how I used to do it with Gentoo, but nothing happens, the card doesn't respond to anything. If i then hibernate and turn back on, lo and behold everything works as per usual. Any ideas? This is getting to be very annoying. Also I have noticed it hangs when "Starting Ubuntu" comes up on screen for about 30 - 40 seconds. This never used to happen so I have no idea what to fix as there is no error msg. Also I have to manually end the configuring network stage in boot with Ctrl C, as it will not go past this point, I guess because the wireless card is being useless and not responding to anything. 

Oh yeah, the reason I installed the gnome app was because I needed to switch between lots of wireless nets quick, instead of using iwconfig. 

I'm loving Ubuntu though: even after this minor hitch which was probably caused by me some how

I would appreciate any ideas very much.
Thanks

P.S. I also installed cross over office? Could this have anything to with it? I just couldnt get used to open office.. lol

---

### Post by sadza on 2005-07-01
Well if it helps anyone else out there gtkwifi seemed to be messing up everything. I uninstalled it and it was back to using iwconfig to configure wireless everytime I turn my laptop on.

---

