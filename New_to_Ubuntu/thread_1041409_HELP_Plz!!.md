---
title: "HELP Plz!!"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by joshp93 on 2009-01-16
Hi i'm a new Ubuntu 8.10 (Dual Boot) user and i have done a very stupid mistake, i was trying to uninstall a OSX style dock but i have uninstalled ubuntu-desktop which is the toolbar and status bar.  All apps are still installed but i cannot access them.

I jave tried to reinstall it via Aptitude in terminal but i cannot connect to a wifi network as the toolbar is missing.

Any help as to connecting to a network would be helpful, or a downloadable ubuntu-desktop .deb file i can download on windows for a flash drive to install in Ubuntu.

any advice would be great, ps im quite new so answers in noob terms please :).

thanks in advance.

---

### Post by mapes12 on 2009-01-16
Can you run a network cable to your router? Ubuntu should then pick up a DHCP address to get you online.

---

### Post by joshp93 on 2009-01-16
great idea will try it, thnx.

---

### Post by sayems on 2009-01-16
All you need to do now is to restore the Ubuntu/Gnome default settings.

Type the following into your command : Alt+F2
[B]
rm -rf .gnome .gnome2 .gconf .gconfd .metacity[/B]

Eventually, do a restart and you should get back the default Ubuntu/Gnome settings!

---

### Post by jamesrfla on 2009-01-16
If you are not getting a IP address do ```
dhcpcd eth0
```

---

### Post by joshp93 on 2009-01-16
Cheers all works like a charm now just Ethernet cabled it nd did the reset settings and is gd.  Fnx for the quick replies!!

---

