---
title: "Autologin locked me out!"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by kladogen on 2009-11-16
Help! I'm locked out of ubuntu!
I have 9.10 server installed. I changed the system to autologin and now after reboot I just get the orange screen and a message  that I have to create the directories /home/antonis/Desktop and /home/antonis/.nautilus because Nautilus cannot work. It seems that my home folder is not mounted and the whole system is stuck. I cant even get a command prompt.
What can I do about this?

---

### Post by ArinSky on 2009-11-16
run a live session and get rid of the auto login temporarily, and try setting it up again.

---

### Post by kladogen on 2009-11-16
Fixed it. It seems it is a bug with auto login and encrypted home files. 
To fix it I entered Recovery Mode from GRUB (hold shift while GRUB loading) and then edited the /etc/gdm/custom.conf file. There I changed the AutoLoginEnable to false.
That way I have to login again but at least I have the system back. Now I must find how to disable home encyption in order to set autologin true again.

---

