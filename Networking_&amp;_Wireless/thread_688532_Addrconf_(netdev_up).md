---
title: "Addrconf (netdev_up)"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by formol on 2008-02-05
hi

i updated the header, and, wifi stop to work.
from dmesg :
ADDR(NETDEV_UP): wlan0: link is not ready

someone can help me? 
(thank you)

---

### Post by formol on 2008-02-05
maybe some info are missing to people to help me...

i'm using ndiswrapper 1.44 ([http://ubuntuforums.org/showthread.php?t=527619&page=4](http://ubuntuforums.org/showthread.php?t=527619&page=4))

and wlan0 is present in ifconfig.  everything seems to be working but it don't, please help me.

---

### Post by wahr on 2008-02-19
I've recently run into this problem and i've implemented a quick fix by opening a term and typing

sudo modprobe ath_pci
sudo ifconfig wifi0 down
sudo ifconfig wifi0 up

i know it's been a while, but I hope this helps out

---

### Post by formol on 2008-02-19
hi,

thx for reply.

oh, i didn't try to set it down before.

just to be sure, you are using ndiswrapper and update the kernel header and then, no wifi?

(because now on my laptop, i've to update kernel header again...)

---

### Post by wahr on 2008-02-19
no, my particular issue was a switch out to daily hardy builds, and I use madwifi.

It's good to know it's not the drivers though.

i get pretty much the same error whenever I resume from sleep, and after considerable poking and prodding came up with that.

(hehe. the irony. I swapped to the dailies to get rid of an annoying backlight keys on resume issue, only to have to do the same manual prodding for the network :P )

---

