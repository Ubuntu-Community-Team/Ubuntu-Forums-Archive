---
title: "still no connection..."
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by uae_83 on 2007-10-28
hi
i still can't get any connection
in the xp version the connection is fine
but on the ubuntu i can't
what should i do
anyone..plz help..:(

---

### Post by winh8r on 2007-10-28
hi there!
best thing to do is post what kind of computer you have and what type of internet connection(modem etc.) That way people can see where your problem might be.
Also post what you are doing to try and connect- you may just be missing something small.
Good luck and keep trying.

---

### Post by uae_83 on 2007-10-28
i've got a cable modem webstarDPC 2100 series

my pc is a 2.4GHZ quad core 2 GB ram
with a gb 8600 motherboard

---

### Post by jenhsun on 2007-10-28
Go to System/Preference/Hardware Information and check your network card.
Is that working? eth0 or eth1
Then
sudo gedit /etc/network/interfaces and bring up your setting.

if your pc get ip automatic try

# the loopback interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

if your pc has static ip, try

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.0.18
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1

---

