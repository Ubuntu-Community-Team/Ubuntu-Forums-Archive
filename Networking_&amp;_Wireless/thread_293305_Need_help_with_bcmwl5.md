---
title: "Need help with bcmwl5"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by mrrobertbates on 2006-11-05
I'm having a problem getting my wireless card to work.  It's a broadcom 1390 on a Dell e1505.  I installed the latest version on ndiswrapper from source. I blacklisted bcm43xx.  I added ndiswrapper to the modules.  Ndiswrapper tells me that bcmwl5 is installed and that hardware is detected, but the wireless card light does not come on!  Dangit!

---

### Post by squibT on 2006-11-05
Try /etc/init.d/networking restart now...then see if you got Internet...also is there a wireless button on your laptop you need to push?

You don't say what you did so just verify you did all the below:

sudo ndiswrapper -l (verify installation complete...see output below)
	>>squibT@laptop:~$ ndiswrapper -l
	>>Installed drivers:
	>>lsbcmnds                driver installed, hardware present 
			
loading the new driver module:
        a) sudo depmod -a 

        b) sudo modprobe ndiswrapper
        

check for error messages:

        a) sudo tail /var/log/messages

set ndiswrapper to load on startup 
	sudo ndiswrapper -m
	gksudo gedit /etc/modules
	* Add the following module to the list at end .... ndiswrapper

to get it going, be sure to 'blacklist bcm43xx'
	a) edit sudo /etc/modprobe.d/blacklist and add <blacklist bcm43xx> to the bottom, no <> please

If at reboot wl does not start add the line: "/etc/init.d/networking restart" (sudo not needed, no quotes) to /etc/rc.local. This will run at startup. No permission changes needed on rc.local file either.

---

### Post by mrrobertbates on 2006-11-05
Thanks alot!  I got it working.  Man these Ubuntu forums are awesome!

---

### Post by Anarkuz on 2008-04-12
Great!  you are a Genius, it works like magic, Thx! 
_______________________________________________________
HP Pavilion zd8000 Series, Broadcom Wireless 802.11 a/b/g WLAN

---

