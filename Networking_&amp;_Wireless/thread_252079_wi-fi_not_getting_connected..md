---
title: "wi-fi not getting connected."
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by viuks on 2006-09-06
Hi.

I have been using this card on ubuntu with no problems. But now I reinstalled my system and never again got IP adress. I am not using any encription. My wifi card is listed in "Network settings" as ra0. Network applet shows, that there is good signal. Ubuntu founds my ESSID, but never connect to it. In */etc/network/interfaces* there is no ra0 listed. If I leave wifi interface in "network settings" as active, then after rebooting system never load gui, but hangs showing only mouse cursor arrow.

Please if someon can point on something useful to help me get ready with this. I am realy stuck.](*,)

---

### Post by x64Jimbo on 2006-09-06
What happens if you boot from the LiveCD? if it works, I strongly recommend that you copy all relevant config files from the LiveCD's filesystem to your hard disk, replacing your current ones.

---

### Post by viuks on 2006-09-06
I have tried many times reinstall system. And once (I don't know how and why) I got wifi connected. It was from live CD, but after install - nothing. And now I can not get wifi from live CD too. Mystics. How coud it be?

---

### Post by viuks on 2006-09-08
I can not believe it. The same problem is on my laptop with different wifi card. So in result I have on my wifi 2XP computers, 1 ubuntu. 2 fresh installed  ubuntu computers can see network, but never recieved ip from DHCP. Mybe it is router problem, bu i do not know how to find or fix it. Please, I realy believe, there is some people, who can help me :-?

---

### Post by wieman01 on 2006-09-08
Ok, 2 questions:

1. Have you got MAC filtering enabled?
2. Can you post this file: /etc/network/interfaces

That could help...

---

### Post by viuks on 2006-09-11
> **wieman01 said:**
> Ok, 2 questions:

1. Have you got MAC filtering enabled?
2. Can you post this file: /etc/network/interfaces

That could help...
1. No. MAC filtering is not enabled.
2:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

Mine wifi has to be ra0, but there is not. I tried manually, but with no joy.

---

### Post by wieman01 on 2006-09-11
Again 2 questions:

1. What wireless card are you using?
2. What's your ESSID?

---

### Post by Ralphthedog on 2006-09-11
ra0....looks like a ralink chipset? You will probably need drivers that support it properly.

[http://www.ubuntuforums.org/showthread.php?t=240669&highlight=ralink+drivers](http://www.ubuntuforums.org/showthread.php?t=240669&highlight=ralink+drivers)

---

### Post by lupine_nickt on 2006-09-12
Definitely ralink ;). 

The drivers work, but are out of date... see if you can get away with just using the rutilt (package ralink-config) utility for configuration.

xF,

...Nick

---

### Post by wieman01 on 2006-09-12
Guys, what's telling you Viuks is using a Ralink device? I can't even see what adapter he is using. Might as well be that we are talking about the wrong driver.

Viuks... Could you point out which card (brand, model, etc.) your are using?

---

### Post by viuks on 2006-09-13
> **wieman01 said:**
> 
Viuks... Could you point out which card (brand, model, etc.) your are using?
Brand is EUSSO, using Ralink chipset. This card worked fine before reinstalling.

My ESSID is D-Links default - dlink.

---

### Post by wieman01 on 2006-09-13
Ok, try this and restart (interfaces):
> auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp
wireless-essid dlink
If this still does not work, deactivate and activate your wireless connection using Gnome's networking tool.

---

### Post by viuks on 2006-09-14
YES! I got my wifi back. Dont ask how, but thanks for help and attention!:cool:

---

