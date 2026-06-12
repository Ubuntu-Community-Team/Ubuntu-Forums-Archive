---
title: "nas network drive is not detected"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by gandaran on 2009-05-14
I have a router with nas server, if I go to places » network theres nothing there except windows network icon, but if I boot the PC windows xp partition first (no problem in windows the nas drive is fully detected) logout and boot ubuntu 9.04 next then in places » network I can see the server drive and mount it!
I don't understand what windows xp does to the drive, map it or something?
but if I switch off the router/server then I have to boot xp again to make it work in ubuntu! amazing!
how can I make it work in ubuntu, maybe I need to install something, but what?
thanks

---

### Post by bacardiandwatermelon on 2009-05-14
What happens if you goto the nas ip address?

---

### Post by gandaran on 2009-05-14
> **bacardiandwatermelon said:**
> What happens if you goto the nas ip address?
in firefox url bar or in places » connect to server? 
I don't have a nas ip, it's the same one as the router ip.
in firefox I can  access it via ftp with the dynamic ip address.

---

### Post by LowSky on 2009-05-14
do you have SAMBA installed?

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by gandaran on 2009-05-14
I don't know what exactly I did but it seams to work now, only problem now is that the nas drive only stays mounted for about 5 minutes then I cant access it anymore, have to unmount the unaccessible drive then click again in places » network » my server and with some luck get it to mount again for another 5 minutes!
this is about the only thing that I fill disappointed with ubuntu

---

### Post by gandaran on 2009-05-15
found a simple solution for this, no need to install anything, just bookmark the mounted drive in nautilus, rename it (Server) now I  can open the nas server drive anytime in nautilus file system whether the server is detected or not in places » network!

---

