---
title: "WEP &amp; KDE wallet"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by flowersrj on 2007-03-31
Hi,

I got a few problems with wireless & WEP.  I amd hoping someone get help me to learn to fix it and understand why.  I am using Feisty Fawn Kubuntu.

1. I have tried to remove KWalletManager but a daemon continues to remain.  At boot, sometimes it prompts me for password.  Anyone know how to remove it?

2. I have put the following in my INTERFACES file so I would not be prompted to connect using WEP but it doesn't seem to work.  It does not seem to look at the password to automatically signin to my WEP router.  Not sure if KWalletManager is the problem.   If I disable WEP it works.  If I reinstall KWalletManager I can get it to work too.  I want it to automatically use wired connection when plugged in and wireless when I am not?  Am I doing something wrong?

auto lo
iface lo inet loopback
address 127.0.0.1

auto eth0
iface eth0 inet static
	address 192.168.1.199
	netmask 255.255.255.0
	gateway 192.168.1.1

auto eth1
iface eth1 inet static
	address 192.168.1.199
	netmask 255.255.255.0
	gateway 192.168.1.1
	wireless-essid NotAvailable
	wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Thanks for looking,
Rich

---

### Post by jedd on 2007-03-31
I had the same problem in gnome, so I removed network-manager and instaled wifi-radar, its helped for me
you can try it ;)

---

