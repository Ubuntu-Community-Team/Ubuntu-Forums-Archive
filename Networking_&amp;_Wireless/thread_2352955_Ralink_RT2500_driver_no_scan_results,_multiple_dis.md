---
title: "Ralink RT2500 driver: no scan results, multiple disconnects"
date: 2017-02-17
forum: Networking &amp; Wireless
---

### Post by ddombrowsky on 2017-02-17
This is similar to [https://ubuntuforums.org/showthread.php?t=1552922](https://ubuntuforums.org/showthread.php?t=1552922) and others, but those are closed threads so I can't post what worked for me.

Version: 4.8.0-37-generic #39-Ubuntu 16.10, yakkety yak

The Ralink wireless cards in question are very old, and the drivers are no longer maintained and don't seem to work very well.  I'm posting this just to show what worked for me as a workaround, while I find an extra $30 to buy a wireless card from this decade.  

When the link drops, I often see things like this in dmesg:
```

[ 1894.144032] ieee80211 phy0: rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16)
[ 5883.248059] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
               Please file bug report to http://rt2x00.serialmonkey.com

```

The wireless will then not scan or connect to anything.  To reset it, try unloading the module, reloading it, and then reset the card to ad-hoc mode.  You also need to turn of the radio before changing the mode.  This is done by setting txpower to off.  Turning off the power management feature also makes the connection a *little *more reliable. Try this as root:

```

modprobe -r rt2500pci
modprobe rt2500pci
iwconfig wlp5s2 txpower off 
sleep 3 
iwconfig wlp5s2 mode ad-hoc
sleep 3 
iwconfig wlp5s2 txpower auto
sleep 3 
iwconfig wlp5s2 power off

```

It should then rescan and connect.  Sometimes it takes multiple tries before it gets into a workable state.  This isn't a solution, but it will allow you to limp along until you get a new wireless card.

---

