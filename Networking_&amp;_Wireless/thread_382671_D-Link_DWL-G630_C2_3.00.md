---
title: "D-Link DWL-G630 C2 3.00"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by DarkEye on 2007-03-12
i finally managed to install this wireless card in my laptop with madwifi.

it seemed to work (the card's leds were flashing like they should), but the internet just wasn't working. i tried to reboot my system and it halts at halfway loading that orange bar from ubuntu. i tried entering recovery mode and it hangs at "configuring network interfaces". i read something about is, but i can't get past it, i can't ctrl+c, i can just reboot.

any help would be appreciated, ubuntu version is 6.10, edgy eft

thanks in advance

---

### Post by DarkEye on 2007-03-12
up, anyone, i really donno how to get out of this :(

tried to remove the network cable, the card, disabling it in bios, but nothing seems to work...i'm really stuck :(

---

### Post by chili555 on 2007-03-12
deleted

---

### Post by DarkEye on 2007-03-12
still noone ? no ideas ? :confused: :)

---

### Post by spd106 on 2007-03-12
Can you boot with a live/desktop cd?

You could try following these instructions [http://www.ubuntuforums.org/showthread.php?t=306424](http://www.ubuntuforums.org/showthread.php?t=306424)
ignore the feisty references, it should still work.

---

### Post by DarkEye on 2007-03-13
i managed to boot from livecd, i did apt-get update, apt-get upgrade and apt-get dist-upgrade but it still doesn't work ... any other ideas

maybe i should post here what is in my /etc/network/interfaces ?

---

### Post by DarkEye on 2007-03-13
noone ?

i uninstalled madwifi, deleted wpa_supplicant, changed /etc/network/interfaces to the /etc/network/interfaces i have on the livecd but still not working...:mad:

---

### Post by DarkEye on 2007-03-13
figured it out after a lot of reading ...

first i fully emptied my /etc/network/interfaces, managed to boot into my system, activated from network options wireless and wired connections (wifi0, ath0, eth0, lo), installed madwifi again, installed wpa_supplicant, and disabled ipv6 ...

it finally works, thread closed :)

---

