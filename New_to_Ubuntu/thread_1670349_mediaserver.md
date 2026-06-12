---
title: "mediaserver"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by adver on 2011-01-18
I am have a hard time changing permissions on files in my media server application. Using Setuid chmod user group -rwsr-xr filename gives a "Operation not permitted" message. I also tried chmod 777 to enable rwx for user group and other and it gives the same message.    The appllication is ps3mediaserver.  I mean mediatomb, not ps3mediaserver, I tried that one and it freezes my pc everytime I run it.

---

### Post by Wobblybob on 2011-01-26
Are you using sudo? something like

$ sudo chmod 777 -R /path to your/Directory

the -R is for sub folders, be careful though when changing permissions you can break stuff, see this link [[COLOR="Purple"]https://help.ubuntu.com/community/FilePermissions[/COLOR]]("https://help.ubuntu.com/community/FilePermissions") for help..

---

