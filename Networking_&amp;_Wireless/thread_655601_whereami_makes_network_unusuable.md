---
title: "whereami makes network unusuable"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by rrwo on 2008-01-01
Whenever I install whereami, nothing on any network is reachable. I cannot even ping the gateway on my router.

I've also noticed that it leaves network interfaces up that should not, such as wired interface when it's not plugged in.

This occurs even with an empty whereami.conf file, so I'm sure it's nothing to do with the selected actions.  (I've tried manually saying things like
```
!lan            ifconfig eth0 down
!lan            resolvconf -d eth0

```
but this doesn't help either.

The detect.conf script seems to correctly detect my network settings. I've tried changing testmii to testreceivefd etc. as I've heard it has problems with gigbit ethernet cards, but to no avail.

Can someone help?

My detect.conf (with exact addresses and SSIDs changed) is below:
```
default undocked

testreceived eth1 wlan
always testmii eth0 lan

if wlan
  set INTERFACE eth1
  testssid HomeNetwork home-wlan
  testssid WorkNetwork work-wlan
fi

if lan
  set INTERFACE eth0
  testarp  eth0,00:01:02:03:04:05,192.168.1.1	home-lan
  testdhcp '10.10.*.*'			work-lan
fi

if home-lan
  at home
elif home-wlan
  at home
fi

if work-lan
  at work
elif work-wlan
  at work
fi

```

I should add that if I do the following, the network is fine:
```

sudo apt-get remove whereami
sudo ifdown eth1
sudo ifup eth1

```
Similarly, merely installing whereami breaks the network. ifup says that it gets an IP address from the router, and gives no errors.

I've looked at the routing tables, and they look fine.  I can't figure out what exactly is broken about the network.

Sometimes it does work, but if I re-run whereami, or hibernate and then resume, it stops working.

For what it's worth, my network interfaces is
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
 pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
 post-down killall -q wpa_supplicant

```

---

### Post by rrwo on 2008-01-03
UPDATE: I've switched to using guessnet instead. It works much better for my needs. So my problems here are moot (at least until I switch back to using whereami ;)

---

