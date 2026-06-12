---
title: "Remote Login from XP - Auth Failed"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by Gripp on 2008-05-15
i set up ubuntu to allow remote access through the preferences menu (vino?)  i set a password and set my router to send calls at that port to this computer.. 

i got to work today and tried yo log in with both VNCviewer 3.3.1 and UltraVNC
my PW is =< 8 characters and i typed it really slowly to make sure i got it right. ... 
my work comp is XP behind a server, but i dont know if that effects anything here...

> ps aux | grep vino

gripp  14231  0.1  0.3 155524  7984 ?        S    22:09   0:00 /usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf-ior-fd=23
gripp  14466  0.0  0.0   5160   832 pts/0    R+   22:12   0:00 grep vino

so apparently it is working. 
i do get the PW prompt, but it tells me that "authorization failed"
i tried variations of my PW as well.. nothing worked...

please help!  thanks

---

