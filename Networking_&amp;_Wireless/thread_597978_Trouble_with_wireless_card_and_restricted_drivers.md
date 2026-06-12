---
title: "Trouble with wireless card and restricted drivers"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by MikeWanDo on 2007-10-30
I seem to have a bit of problem here.  I'm using a broadcom wireless card with a fresh install of Gutsy and it Ubuntu sees just fine.  The only problem is that in order to get it working I have to install the restricted driver firmware.  Now I would have no problem doing this but Ubuntu can't connect to the internet to download the firmware.

I don't really want to move my computer, modem or wireless card to get it set up.  I am however booting from my USB drive currently (thankyou for all the great guides out there) so If there's a way to install the firmware on my wired computer and then apply it when I move the USB to my wireless computer that'd be great.  Does anyone know how to do this or have another way to install the restricted driver offline while my USB is in the wireless computer?

---

### Post by spd106 on 2007-11-01
Sure, you can download the firmware file from [here]("http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o"), then transfer it over to your other computer via USB disk.

If you have a Windows driver CD, that may also work as well, but the above file is the one recommended by the bcm43xx developers. See [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

