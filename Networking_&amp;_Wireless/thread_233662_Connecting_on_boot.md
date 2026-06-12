---
title: "Connecting on boot"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by boscopup on 2006-08-10
I have a Broadcom 4306, and have used the bcm43xx-fwcutter method of getting it running. So all is good with that. I set up the details in the Networking section of Administration, and it's set to do DHCP and look for the appropriate named AP. The problem... After rebooting, I have to do the following to get it running again:

```

$sudo iwlist eth1 scan
$sudo dhclient eth1

```

The first line has to be done because the AP is listed as "Invalid' when typing 'iwconfig'. The second one is done because it apparently doesn't do DHCP when it comes up, even though my interfaces file says dhcp in it. :confused:

Here's the contents of my interfaces file:

```

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid xxxxxxxx

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

(where "xxxxxxxx" is the actual essid)

So do I need to edit something in the interfaces file? I'm a newbie to Ubuntu, and have been out of the Linux world for a couple years, so I'm pretty rusty. :)

---

### Post by boscopup on 2006-08-12
Bumpity-bump... Anyone? Let me know if I need to post more info.

---

