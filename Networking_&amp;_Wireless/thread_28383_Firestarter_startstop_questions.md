---
title: "Firestarter start/stop questions"
date: 2005-04-19
forum: Networking &amp; Wireless
---

### Post by Turin Turambar on 2005-04-19
I'm using a dial-up PPP connection. I configured firestarter to start when my connection begins. However, after I disconnect, it is still running. Is there a way for me to make it stop after I disconnect?

Also, during reboot/shutdown phase, the system tries to stop firestarter and reports error "ppp0 device not found". I guess that's normal, since I'm not connected - ppp0 does not exist.

Why the system tries to stop firestarter even if I stop it manually in Gnome? Can I do something about those errors, or they are inevitable?

Thanks.

---

### Post by ming0 on 2005-04-20
[QUOTE=Turin Turambar]Why is it still stopping firestarter if I stop it manually in Gnome? [/QUOTE]

I think that firestarter might still run as a daemon, even after you shut it down in gnome.

Just forget about using a firewall, and do it the MS way! ;) (just kidding)

I have a similar gripe with firestarter complaining that my wireless connection isn't on (when really I just need to press a button to connect up to my AP) Hopefully the firestarter devs fix this, and make it so that all this junk happens under the hood.

---

