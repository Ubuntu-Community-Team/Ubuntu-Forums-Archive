---
title: "Static IP does not work with Networking GUI"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by monomaniacpat on 2007-02-17
I would like to set my ubuntu box to a static IP, so that I can more easily set rules for my router. However, whenever I try to add a static IP to the Networking GUI (under System>Administration) the box pretends to connect to the network when I click enable, but it is in fact not connected, as I cannot browse with firefox. It is suspicious also because it does it instantly, rather than the 20 seconds wlan usually takes to connect to the router. 

I have no problems as long as it is set to DHCP, but as I've already explained I do not want to use DHCP. I have other devices connected with a static IP, so it's presumably nothing to do with the router.

Shouldn't this really be quite straightforward?

---

### Post by aa.ivanov on 2007-02-17
Unless you are using NetworkManager or something alike you can always do it the hard way - set the address in /etc/network/interfaces.

It should look like this:
```
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
```

Of course you should write your address, netmask and gateway in accordance to your network environment. If you have more than one network card you should specify which one - eth0, eth1.... If you have just one network card - it is eth0.

---

### Post by monomaniacpat on 2007-02-20
Thanks for the reply. I tried what you suggested but sadly it did not work.

Here is my interfaces file as it stands (I use a wireless connection wlan0):

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid *********
wireless-key **********



auto wlan0

```

I am using network-admin...

---

### Post by monomaniacpat on 2007-02-20
Just realised what I did wrong - I had left the "iface wlan0 inet" as dhcp. Just changed it to static as aa.ivanov suggested and it worked a treat! Thanks!

Maybe it didn't work with network-admin because it was conflicting with the interfaces file?

---

