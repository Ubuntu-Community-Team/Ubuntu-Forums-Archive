---
title: "acx/ndiswrapper problem, not detected"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by nol13 on 2006-09-12
Hi, I had my wireless setup with ndiswrapper and everything worked great until I upgraded to dapper. After the upgrade internet didnt work but after i replaced "tiacx111c16" or something and it worked, kinda. But, it is now using the ACX (used to be acx_pci in hoary) driver instead of ndiswrapper so my internet has been a slow slow crawl. ndiswrapper still shows up under lsmod and it still says that the hardware and driver are present. When i rmmod ACX though and then re-setup ndiswrapper iwconfig can't find "wlan0" until i modprobe ACX again.

So how do i get ubuntu to recognize ndiswrapper as the wlan0 driver again?

---

### Post by NetworkGuy on 2006-09-12
Look into this howto.  You no longer need to use NDISWRAPPER.  

[http://www.ubuntuforums.org/showthread.php?t=233565](http://www.ubuntuforums.org/showthread.php?t=233565)

I got my card up and running in under 3 minutes using this howto.

---

### Post by nol13 on 2006-09-13
Did all that stuff, my problem is that the OS acx driver that ubuntu comes with is unbearably slow (dial-up speeds). Are you getting a normal connection with that driver?

ndiswrapper is definitly still nescessary for me.

never had a problem with this before the dapper upgrade or on any other distro, but since the upgrade my system seems to be ignoring ndiswrapper completely. very frustrating.

---

