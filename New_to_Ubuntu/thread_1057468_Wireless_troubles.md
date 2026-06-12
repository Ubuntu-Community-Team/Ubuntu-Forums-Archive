---
title: "Wireless troubles"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by OwenDW on 2009-02-01
Hey guys, just installed Ubuntu 8.10 on my laptop and am having troubles with wireless connections. Ethernet is fine, however wireless, although when I look in hardware drivers, it says that no proprietry drivers are in use but there is support for Atheros 802.11 wireless LAN cards.

I have an  Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter.

So, any ideas on how to set up my wireless? Was reading a thread last night which said to download "ath5k" from the Intrepid backport page but I couldn't see it listed. Any help, please?

---

### Post by shifty_powers on 2009-02-01
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

should start you off

---

### Post by OwenDW on 2009-02-01
Shifty,

Thats the wiki I found last night, followed the links to the backport page and still couldn't find anything regarding "ath5k" so gave up around 2am.

If I can find the ATH5k doo hickey thing, I might be able to get somewhere! Don't suppose you would know where it might be hidden?

Thanks,

Owen.

---

### Post by Crafty Kisses on 2009-02-01
See if this thread doesn't help you: [http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860).

---

### Post by shifty_powers on 2009-02-01
[http://ubuntuforums.org/showthread.php?p=6089169](http://ubuntuforums.org/showthread.php?p=6089169)

is a better explanation. do

```
sudo apt-get install linux-backports-modules-intrepid
```

then

```
gksudo gedit /etc/modprobe.d/blacklist
```

and add

```
blacklist ath_hal
blacklist ath_pci
```

at the bottom of the file and reboot.

then go System/Administration/Hardware Drivers make sure Atheros driver is activated.

---

### Post by OwenDW on 2009-02-01
Shifty, thanks for that! Wireless networks are now appearing!

I only needed to install the intrepid backport though, and not follow through with the other steps. I don't suppose anyone would be able to tell me the point of the commands? Obviously the first one is installing things, however what is the point of backports anyway?

If I don't remove the blacklist (If the ath5k is blacklisted, I didn't see it there before) from ath5k, am I likely to get issues further down the road?

Thanks a heap guys!!

Off to enjoy my first cup of Ubuntu :)

---

