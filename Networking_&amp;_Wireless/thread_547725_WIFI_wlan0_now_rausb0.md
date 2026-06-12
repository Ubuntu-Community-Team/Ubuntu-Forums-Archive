---
title: "WIFI wlan0 now rausb0"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by kell05 on 2007-09-10
I am trying to get my USB wireless card to work.  I have had the card working before under the interface wlan0 however after I rebooted my computer it would not work and the interface wlan0 was not avialable however rausb0 was there.  I then ran sudo dhclient rausb0 but it would not connect to the router.  Thank you for your help.

P.S. This is the set of instructions that I followed and repeated to get it working the first time and then repeated without working.

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by Zorael on 2007-09-10
If it's just an issue of the interface assuming the wrong name, you can rename it by editing /etc/iftab. It should just be a matter of finding the rausb0 entry and reverting it to wifi0 again.

I don't think there's a GUI alternative, you likely have to poke around with the terminal.

---

