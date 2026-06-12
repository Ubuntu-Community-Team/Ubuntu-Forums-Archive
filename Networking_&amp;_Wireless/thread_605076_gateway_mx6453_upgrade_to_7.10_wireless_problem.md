---
title: "gateway mx6453 upgrade to 7.10 wireless problem"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by kitchenn on 2007-11-06
I have just recently upgraded to the new ubuntu gutsy from the previous version fiesty.  I had gotten my wireless card to work using ndiswrapper in fiesty but when I made the switch to gutsy my wireless no longer shows up under eth0.  I kept my original blacklist file from fiesty.

ndiswrapper -l says that:
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

The ati restricted driver also does not support any of the desktop effects, although this is not a priority at the moment.

Any help getting this problem fixed would be appreciated.
Thanks

---

### Post by Lambert on 2007-11-07
When you say you upgraded to gutsy, did you go through the ndiswrapper install procedures? Even though it says its installed, there's a new kernel with gutsy and you have to go through the install procedures again for ndiswrapper.

---

### Post by kitchenn on 2007-11-08
Yeah, I did did an uninstall of ndiswrapper and a fresh build, I rebuilt the bcmwl5 driver using ndiwrapper and its still give me this message for ndiswrapper -l

bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

I have the bcm43xx driver blacklisted, and when I do a "sudo rmmod bcm43xx" it says that the modules not there.  I kept my orignal /etc/modprobe.d/blacklist file so I'm not sure if thats creating any conflicts.  I also have the ndiwrapper file creating the alias wlan0 so I'm not sure what else to modify to get this working.

If you load the unrestricted driver for bcm43xx would that create any conflicts I might have to resolve?

---

### Post by 0o_dude_o0 on 2007-11-10
i have same gear, exact same problem

---

