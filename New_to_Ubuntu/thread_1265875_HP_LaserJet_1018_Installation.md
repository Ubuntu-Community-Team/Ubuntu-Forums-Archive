---
title: "HP LaserJet 1018 Installation"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by noorez on 2009-09-14
My Hp laster jet 1018 has been having some pretty random behaviour....sometimes I can print just fine, sometimes I can't....when i can't I usually have to reinstall the printer..

To try and fix this I downloaded and installed the hp installer: hplip-3.9.8.run for ubuntu 9.04 and hp lasterjet 1018.

I managed to install it and the hp-setup utility found my printer on the usb connection and added it. 

However I still cannot print anything.....when i open the print queue dialog in the notification area, there is message saying that the printer may not be connected or turned off......but it is both connected and turned on!  I know this because I could add the printer...

anyone have any ideas?

---

### Post by horobi on 2009-09-22
same problem here

---

### Post by marchwarden on 2009-09-22
I had the same problem with the same printer a week ago.  I ended up re-installing the Windows driver (dual-boot system) and for some reason that fixed it, it may have something to do with the printer firmware.

---

### Post by horobi on 2009-09-22
i fixed it

before doing anything i removed foo2zjs

> sudo apt-get remove foo2zjs

then i tried replacing fooz2js with this one:

[http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/")

and following this guide:

> UBUNTU NOTES
------------
    Install build-essential FIRST:
	$ sudo apt-get install build-essential
	$ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
	$ tar zxf foo2zjs.tar.gz
	$ cd foo2zjs
	$ sudo make uninstall
	$ make
	$ ./getweb 1080
	$ sudo make install install-hotplug cups

	For 7.10 and later users:
	    $ sudo system-config-printer

	For 5.10/6.06/6.10/7.04 users:
	    $ sudo gnome-cups-manager
	    [configure ColorMode = Color if a color printer]
	    $ sudo make cups

	    Ubuntu has a bug in gnome-cups-manager with Color, so you must
	    restart cups.  No other distro has this bug.

    If that doesn't work, then fire up:
	$ firefox [http://localhost:631](http://localhost:631)

	And click on:
	    Printers -> Set Printer Options -> Color Mode -> Color
	Then click on:
	    Set Printer Options

with no luck, so i tried removing completely foo2zjs with

> sudo make uninstall

then i downloaded HPLIP from [http://hplipopensource.com/hplip-web/index.html]("http://hplipopensource.com/hplip-web/index.html")

i installed it following script messages and the printer started working

;)

---

### Post by LowSky on 2009-09-22
use this method to install
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

dont forget to turn off  and pull the cord on the printer and reboot, then plug back in.

this method works everytime

---

### Post by feranick on 2009-11-25
Alternatively, open the printing panel (System->administration->printing), and with the printer connected double click on the printer icon. Change the driver from the "Foomatic/foo2zjs"  to the "HP LaserJet 1018 hpijs, 3.9.8". This works every time, no compilation, no reboot. Tested and working with Karmic.

---

