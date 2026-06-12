---
title: "guessnet problem"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by l_b on 2008-05-02
Hi all,

I'm trying to setup guessnet for automatically configuring my (wireless) network interface. But I can't get it working.

I have two interfaces: eth0 & wlan0

This is my /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto wlan0
mapping wlan?
  script guessnet-ifupdown
  map default: none
  map timeout: 9
  map init-time: 9
  map verbose: true

iface home inet dhcp
  test wireless essid USR5464
```

And when I run guessnet, I get the following output:
```

leon@polly:~$ guessnet -i --debug
guessnet: program name is guessnet-ifupdown: enabling ifupdown mode
guessnet: Added startable with priority 10
guessnet: 1 candidates found in input
guessnet: Guessnet 0.47 starting...
guessnet: Trying MII detection
guessnet: Link beat detection (mii) failed: Operation not permitted
guessnet: Link beat detection (ethtool) failed: Operation not permitted
guessnet: Link beat detection (priv) failed: Operation not supported
guessnet: No working link beat detection function available for interface eth0
guessnet: 0 candidate profiles
guessnet: Added "default" test none
guessnet: Initialized test subsystems
guessnet: Starting all 1 startables
guessnet: Starting elements with priority 10
guessnet: Starting wireless scan
guessnet: Started tests
guessnet: 2 candidates
Operation not supported. Context: running the scan.  Quitting IWScan thread.
none

```

Now with wlan0 explicit:
```

root@polly:~# guessnet -i --debug wlan0
guessnet: program name is guessnet-ifupdown: enabling ifupdown mode
guessnet: Added startable with priority 10
guessnet: 1 candidates found in input
guessnet: Guessnet 0.47 starting...
guessnet: Trying MII detection
guessnet: Link beat detection (mii) failed: Operation not supported
guessnet: 0 candidate profiles
guessnet: Added "default" test none
guessnet: Trying MII detection
guessnet: Initialized test subsystems
guessnet: Starting all 1 startables
guessnet: Starting elements with priority 10
guessnet: Starting wireless scan
guessnet: Started tests
guessnet: 2 candidates
guessnet: Found network USR5464
guessnet: Testing wireless essid USR5464
guessnet: Testing wireless essid USR5464: essid passed
guessnet: Testing wireless essid USR5464: match successful
guessnet: wireless essid USR5464 matched network USR5464
guessnet: Found network SpeedTouch3D888A
guessnet: Testing wireless essid USR5464
guessnet: Testing wireless essid USR5464/essid: fail as essid "SpeedTouch3D888A" is not "USR5464"
guessnet: Found network NETGEAR
guessnet: Testing wireless essid USR5464
guessnet: Testing wireless essid USR5464/essid: fail as essid "NETGEAR" is not "USR5464"
guessnet: Found network Heijdens
guessnet: Testing wireless essid USR5464
guessnet: Testing wireless essid USR5464/essid: fail as essid "Heijdens" is not "USR5464"
guessnet: Found network ipaq
guessnet: Testing wireless essid USR5464
guessnet: Testing wireless essid USR5464/essid: fail as essid "ipaq" is not "USR5464"
guessnet: Found network DDBwap
guessnet: Testing wireless essid USR5464
guessnet: Testing wireless essid USR5464/essid: fail as essid "DDBwap" is not "USR5464"
guessnet: Notified success of scan wireless essid USR5464
guessnet: Keeping candidate home
guessnet: End of wireless scan
home

```

When I do /etc/init.d/networking restart, I get:
```

root@polly:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                           guessnet: Link beat detection (mii) failed: Operation not supported
guessnet: 0 candidate profiles

```

Is there something I'm doing wrong?

Thanks in advance!

---

### Post by l_b on 2008-05-03
Changed my "/etc/network/interfaces" to:
```

auto lo
iface lo inet loopback

auto wlan0
mapping wlan?
  script guessnet-ifupdown
  map default: none
  map wlan-home
  #autofilter: true
  map timeout: 9
  map init-time: 9
  map verbose: true
  map debug: true

iface wlan-home inet dhcp
  test1 wireless essid USR5464

```

And now it seems to work. However, if I enable "autofilter" I get the following error message:
```

leon@polly:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
/etc/network/interfaces:9: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:9: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"

```

---

### Post by l_b on 2008-05-06
I've managed to get it working. This is my working configuration:

```
auto lo
iface lo inet loopback

auto wlan0
mapping wlan0
  script guessnet-ifupdown
  map default: none
  map autofilter: true #Look for wlan0- interfaces
  map timeout: 9
  map init-time: 9 #For slow drivers
  map verbose: true
  map debug: true

iface wlan0-home inet dhcp
  test wireless essid USR5464
  wireless-essid USR5464

iface wlan0-tim inet dhcp
  test wireless essid Tim_online closed
  wpa-psk 1912197517
  wpa-key-mgmt WPA-PSK
  wpa-proto WPA
  wpa-ssid Tim_online

#If all else fails: pick an open network
iface wlan0-open inet dhcp
  test wireless open
  wireless-essid any
  wireless-mode auto
```

But now, I've got two networks in the proximity (Tim_online & hotspot). Tim_online is encrypted. Hotspot's not. I want guessnet to choose Tim_online but it keeps picking Hotspot. Why's that?

This is the output of "guessnet-ifupdown -i wlan0 --debug":

```

guessnet: program name is guessnet-ifupdown: enabling ifupdown mode
guessnet: Added startable with priority 10
guessnet: 3 candidates found in input
guessnet: Guessnet 0.47 starting...
guessnet: Trying MII detection
guessnet: Link beat detection (mii) failed: Operation not permitted
guessnet: Link beat detection (ethtool) failed: Operation not permitted
guessnet: Link beat detection (priv) failed: Operation not supported
guessnet: No working link beat detection function available for interface wlan0
guessnet: 0 candidate profiles
guessnet: Added "default" test none
guessnet: Initialized test subsystems
guessnet: Starting all 1 startables
guessnet: Starting elements with priority 10
guessnet: Starting wireless scan
guessnet: Started tests
guessnet: 4 candidates
guessnet: Found network hotspot
guessnet: Testing wireless essid USR5464
guessnet: Testing wireless essid USR5464/essid: fail as essid "hotspot" is not "USR5464"
guessnet: Testing wireless essid Tim_online closed
guessnet: Testing wireless essid Tim_online closed/essid: fail as essid "hotspot" is not "Tim_online"
guessnet: Testing wireless open
guessnet: Testing wireless open: network hotspot isOpen is 1, flags 8000
guessnet: Testing wireless open: open network passed
guessnet: Testing wireless open: match successful
guessnet: wireless open matched network hotspot
guessnet: Found network hotspot
guessnet: Testing wireless essid USR5464
guessnet: Testing wireless essid USR5464/essid: fail as essid "hotspot" is not "USR5464"
guessnet: Testing wireless essid Tim_online closed
guessnet: Testing wireless essid Tim_online closed/essid: fail as essid "hotspot" is not "Tim_online"
guessnet: Testing wireless open
guessnet: Testing wireless open: network hotspot isOpen is 1, flags 8000
guessnet: Testing wireless open: open network passed
guessnet: Testing wireless open: match successful
guessnet: wireless open matched network hotspot
guessnet: Found network Tim_online
guessnet: Testing wireless essid USR5464
guessnet: Testing wireless essid USR5464/essid: fail as essid "Tim_online" is not "USR5464"
guessnet: Testing wireless essid Tim_online closed
guessnet: Testing wireless essid Tim_online closed: essid passed
guessnet: Testing wireless essid Tim_online closed: network Tim_online isOpen is 0, flags 800
guessnet: Testing wireless essid Tim_online closed: closed network passed
guessnet: Testing wireless essid Tim_online closed: match successful
guessnet: wireless essid Tim_online closed matched network Tim_online
guessnet: Testing wireless open
guessnet: Testing wireless open: network Tim_online isOpen is 0, flags 800
guessnet: Testing wireless open/open: failed because network is closed
guessnet: Found network GIGABYTE
guessnet: Testing wireless essid USR5464
guessnet: Testing wireless essid USR5464/essid: fail as essid "GIGABYTE" is not "USR5464"
guessnet: Testing wireless essid Tim_online closed
guessnet: Testing wireless essid Tim_online closed/essid: fail as essid "GIGABYTE" is not "Tim_online"
guessnet: Testing wireless open
guessnet: Testing wireless open: network GIGABYTE isOpen is 0, flags 800
guessnet: Testing wireless open/open: failed because network is closed
guessnet: Found network NHTV-WPA
guessnet: Testing wireless essid USR5464
guessnet: Testing wireless essid USR5464/essid: fail as essid "NHTV-WPA" is not "USR5464"
guessnet: Testing wireless essid Tim_online closed
guessnet: Testing wireless essid Tim_online closed/essid: fail as essid "NHTV-WPA" is not "Tim_online"
guessnet: Testing wireless open
guessnet: Testing wireless open: network NHTV-WPA isOpen is 0, flags 800
guessnet: Testing wireless open/open: failed because network is closed
guessnet: Found network NHTV-GAMELAB
guessnet: Testing wireless essid USR5464
guessnet: Testing wireless essid USR5464/essid: fail as essid "NHTV-GAMELAB" is not "USR5464"
guessnet: Testing wireless essid Tim_online closed
guessnet: Testing wireless essid Tim_online closed/essid: fail as essid "NHTV-GAMELAB" is not "Tim_online"
guessnet: Testing wireless open
guessnet: Testing wireless open: network NHTV-GAMELAB isOpen is 0, flags 800
guessnet: Testing wireless open/open: failed because network is closed
guessnet: Found network ImageMove
guessnet: Testing wireless essid USR5464
guessnet: Testing wireless essid USR5464/essid: fail as essid "ImageMove" is not "USR5464"
guessnet: Testing wireless essid Tim_online closed
guessnet: Testing wireless essid Tim_online closed/essid: fail as essid "ImageMove" is not "Tim_online"
guessnet: Testing wireless open
guessnet: Testing wireless open: network ImageMove isOpen is 0, flags 800
guessnet: Testing wireless open/open: failed because network is closed
guessnet: Found network B-inmotion
guessnet: Testing wireless essid USR5464
guessnet: Testing wireless essid USR5464/essid: fail as essid "B-inmotion" is not "USR5464"
guessnet: Testing wireless essid Tim_online closed
guessnet: Testing wireless essid Tim_online closed/essid: fail as essid "B-inmotion" is not "Tim_online"
guessnet: Testing wireless open
guessnet: Testing wireless open: network B-inmotion isOpen is 0, flags 800
guessnet: Testing wireless open/open: failed because network is closed
guessnet: Notified success of scan wireless open
guessnet: Removing candidate wlan0-home
guessnet: Keeping candidate wlan0-open
guessnet: Removing candidate wlan0-tim
guessnet: We had changes, notifying the listener
guessnet: End of wireless scan
```

---

### Post by jc15 on 2008-06-09
Try to put
map-default=!wlan0-open

instead of 
map-default=none

in mapping wlan0 section

---

