---
title: "Asus EEEPC900 Atheros WEP/WPA can't connect"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by brutaltruth on 2008-11-07
Hi all,

I've installed the eeepc ubuntu 8.04 on my eeepc.
It worked well on my home WEP wireless LAN and on open wireless LANs.

But since about week, I tried to connect it on WPA LANs without success.
Coming back home, I can't connect on my WEP LAN anymore.
I'm still able to connect on open LANs.

I'm sure I've missed something in the configuration, but can't find where.

The ath_pci driver is loaded, I can scan wireless networks, but no more connect.

I tried with standard gnome network manager and wcid.

dhclient keeps trying and gives up.

Regards,
JC

---

### Post by brutaltruth on 2008-11-08
Hi,

I've upgrade my eeepc to 8.10. same problems...
I've tried with the standard network-manager, wicd, wifi-radar, editing config files manually... to no avail.

Regards,
JC

---

### Post by brutaltruth on 2008-11-10
The n00b is back ;)

Still fighting... I recompiled with latest ubuntu kernel, using ath5k driver instead of ath_pci. Still no change.

But I missed something: my wifi access point is using channel 12, iwlist only display up to channel 11 as available on my atheros AR2425.

Is there a way to add channels on my atheros, or is it hardware dependant (so tuning my access point is the only way) ?

---

### Post by brutaltruth on 2008-11-10
SOLVED !

Finally found the goos params for madwifi's ath_info:

./ath_info -v -g 1:0 -w 0xfbef0000 regdomain 0x00

after that, added in /etc/modprobe.d/options:
options ath_pci countrycode=250

and all works well :)

---

### Post by ignitz on 2009-05-12
Thanks

---

