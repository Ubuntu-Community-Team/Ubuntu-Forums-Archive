---
title: "connection discrepancy between ubuntu and windows"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by unready%20cincinnatus on 2007-10-12
My computer shows a huge discrepancy between wireless signal strengths as detected by windows and ubuntu.  Where windows will connect with no complaints, ubuntu will putz around for a minute then give up on the connection.  Ubuntu connects under certain conditions (ie, moving upstairs where the signal is presumably stronger), but Windows always registers the stronger signal.

The computer in question is a Toshiba A85 Satellite using the stock wireless card (Atheros brand).  Madwifi drivers are installed and at their most recent revision.  

The only wildcard I can think of is the network itself.  Is it possible this is an issue with the security implemented by the network?  I live in a college dorm, so I have no control over the access point.  I do remember registering with the IT department when I first arrived on campus, and the wireless card on my desktop doesn't work, presumably because it hasn't been registered.   If it's not the network, and I'm 90% sure it's not the driver, what could it be?

I'm out of ideas.  Help, please!

---

### Post by naazgull on 2007-10-12
Hi,

Could you, please, post the contents of */etc/network/interfaces*?

Cheers,

---

### Post by unready%20cincinnatus on 2007-10-12
$more /etc/networks/interfaces

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

---

