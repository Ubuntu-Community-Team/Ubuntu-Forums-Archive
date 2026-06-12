---
title: "ok im trying to switch over to ndiswrapper instead of bcm43xx"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by darkmdbeener on 2008-02-12
i got everything working. but i cant do the modprobe ndiswrapper 

i get FATAL: could not open '/lib/modules/.../ndiswrapper.ko': no such file or directory what should i do...

ill as that i was runing bcm43xx but it stoped working and i acidentily got it to uncheak in the restrickted drivers part (which i think unistalled it).

and im useing the ndiswrapper 1.50 and 1.9 utils

thank you
EDIT
also i cant conect to the internet at all so im stuck. ever sence the last update the wired network doesnt work.

i have the xp driver instaled and it say something about an alternat driver bcm43xx when i do the ndiswrapper -l


EDIT 
well can someone tell me how to get conected via wired.  for some reason i get a wired IP and will not work 
it started after the update (the xorg)
im pretty sure that it is posible the ndiswrapper version im useing that is makeing things hard.

thank you


FIXED:
sudo apt-get --reinstall install linux-ubuntu-modules-2.6.22-14-generic    
fixed it

---

