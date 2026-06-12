---
title: "Getting wpa_supplicant to run at bootup problem"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by NotExcessive on 2007-02-12
I've been running a PCMCIA card for my wireless connection since I put this laptop together a week ago, and it's been fine. I'm a Gentoo user and all my rack servers run it but for my personal laptop I decided to load Ubuntu 6.10 on it and I love it so far.

The card I was using was a 3Com 3CRWE154G72, v1, and I was using the standard wext driver, which much to my surprise, actually ran the card (with Gentoo on another laptop, I had to use ndiswrapper and the WindoZe driver). Now I've installed an Atheros 5212 internal card and dumped the 3Com, and I'm having trouble getting it to run at bootup.

This was my  /etc/network/interfaces file with the old 3Com card:

[COLOR=Blue]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf[/COLOR]


I installed the Atheros, and changed the file to:

[COLOR=Blue]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp
wpa-driver madwifi
wpa-conf /etc/wpa_supplicant.conf[/COLOR]

Now the odd thing is, I can't get it to run automagically. 

iwconfig shows ath0 with all the right information except that it hasn't associated with the WAP. However, if I do a* killall wpa_supplicant*, and then do things manually:
[I]wpa_supplicant -w -iath0 -Dmadwifi -c/etc/wpa_supplicant.conf
dhclient ath0[/I]

then it launches right away and I'm on the air.

Can anyone tell me why my automagical configuration doesn't work as it used to?

---

