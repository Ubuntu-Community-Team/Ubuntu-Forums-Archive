---
title: "I can't access network settings."
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by Tha_Pig on 2007-12-17
I'm using Xubuntu on a Ramline tablet.

My computer recognized the wireless network card (Belkin) but it could not connect to the wireless network. I tried to change some of the network properties and restarted the computer.

Now I can't open the network properties at all. I click the menu icon and I get the clock cursor for a few seconds... then nothing. I tried both with or without the network card in the slot with the same result.

Is there another way to change the network settings, or reset it to default?

I would appreciate any help.

---

### Post by spd106 on 2007-12-19
Try editing the /etc/network/interfaces file. By default it should look like this.

```
~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

Problems often occur with duplicate lines or missing the loopback.

---

