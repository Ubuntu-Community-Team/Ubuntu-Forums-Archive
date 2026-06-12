---
title: "Set network location as default?"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by Lanevo on 2007-03-11
Hey guys, 

Hopefully a simple question ... How do i set a network location as default, so that when i start up, it is already selected?

thanks 

John

---

### Post by trioj85 on 2007-03-26
I'm looking for an answer to this as well.
My internet connection requires that I enter a DNS server (obviously) but every time Ubuntu reboots the address is lost.

I assume there's a configuration file to edit, just need to know which one it is.

Tristan

---

### Post by stricevics on 2007-03-31
> **trioj85 said:**
> My internet connection requires that I enter a DNS server (obviously) but every time Ubuntu reboots the address is lost.


I had an issue with this as well. I needed an address of my router as a DNS server address. However, every time I would reboot, it would change to something diffrent, completely unrelated to my stuff. The clue was in the Search Domains field, which would at that point be changed to something.comcast.net. At that point I figured that my ath0 (wireless NIC which I do not use at the moment, but it's PCI so it's on) gets the stuff from DHCP server before my eth0, and that comcast stuff is actually from my neighbour somewhere around who has Comcast service. 

So pay a visit to the */etc/network/interfaces* and make the changes according to your configuration.

```
sudo nano /etc/network/interfaces
```

This is how mine looks now:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```

Hope this helps,

St.

---

