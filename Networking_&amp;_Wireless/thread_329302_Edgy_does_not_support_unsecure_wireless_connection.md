---
title: "Edgy does not support unsecure wireless connections"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by xml2k on 2007-01-01
Is the title statement true, it seems so to me. I can connect to my home network only if I have security enabled, but cannot do so if I set it to be unsecured, such as it would be in a library or cafe that has free-wifi. I have even tried to connect at a few free-wifi businesses with no success.

If unsecured connections are possible and you are doing this can you please share your distro version, card and setup.

I am using edgy on a dell inspiron 5100 with a motorola WN825G wireless card.

Happy '007

---

### Post by phossal on 2007-01-01
Many people configure their wireless networks without wep/wpa before securing their connections, even in Edgy.  ;)

---

### Post by haiku99 on 2007-01-01
if all else fails you can manually edit your /etc/network/interfaces file.  I've also used wifi radar to connect to open AP's.  Anyway, this is what my file looks like.....the entry for rausb0 is for a free network...



bill@bill-laptop:~$ cat /etc/network/interfaces


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto rausb0
iface rausb0 inet dhcp
wireless-essid Freenet


auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid Ignatius
wireless-key 1234567890

---

### Post by supermarchino on 2007-03-29
> **haiku99 said:**
> if all else fails you can manually edit your /etc/network/interfaces file.  I've also used wifi radar to connect to open AP's.  Anyway, this is what my file looks like.....the entry for rausb0 is for a free network...



bill@bill-laptop:~$ cat /etc/network/interfaces


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto rausb0
iface rausb0 inet dhcp
wireless-essid Freenet


auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid Ignatius
wireless-key 1234567890

Did your Motorola WN825G card work out of the box with edgy?

---

### Post by trent dillman on 2007-04-03
...

---

