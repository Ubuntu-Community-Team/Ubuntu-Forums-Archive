---
title: "Network manager sees all wireless networks for a few seconds, then none"
date: 2015-08-03
forum: Networking &amp; Wireless
---

### Post by superian on 2015-08-03
I'm using Lubuntu 15.04 on an EeePC 901. Using the home wireless network is fine, but two times in two different places recently, it has seen all the networks for a few seconds and then decided it cannot see any.

(Photos of this are available, but as I can't get scrot to capture the popup list of lots/no networks, they're via a camera.)

Based on two lines in /var/log/syslog ..

```
Aug  2 19:35:45 eee901 kernel: [   23.933607] eeepc_laptop: BIOS says wireless lan is unblocked, but the pci device is absent
Aug  2 19:35:45 eee901 kernel: [   23.933614] eeepc_laptop: skipped wireless hotplug as probably inappropriate for this model
```

.. very late in the start up process I wondered if the wireless card was, for some reason, being ignored from this point, but the wireless script shows that something can still see all the networks here: see its output at [http://pastebin.ubuntu.com/11992165/](http://pastebin.ubuntu.com/11992165/)

Any suggestions?

---

### Post by tgalati4 on 2015-08-04
Try reseating the wireless card.  It may be loose in its slot.  The antenna may be worn out.  It's typically a thin wire that runs from the screen bezel through the hinge to the wireless card.  Has this notebook seen a lot of use?

It could be interference from many networks.  Sometimes cards shut down as a protection when too strong a signal is detected.  Does your notebook have a physical switch to turn it on and off?  If so, turn it off, wait 10 minutes, then turn back on.  Open a terminal and post:

```
dmesg | tail -50
```

---

### Post by superian on 2015-08-04
No, it's not had a huge amount of use and it works perfectly at home before and after the Denmark trip.

There were a lot of visible (for those seconds!) networks in Denmark - the first place I noticed this - but no more than I usually see here. 

No, there's no real switch. A specially shifted key is supposed to do.

[14695.676763] show_signal_msg: 21 callbacks suppressed
[14695.676786] lxpanel[1065]: segfault at 5c ip b4d3d1bb sp bff0ff70 error 6 in netstat.so[b4d39000+8000]
[14696.184639] pci 0000:01:00.0: [1814:0781] type 00 class 0x028000
[14696.184693] pci 0000:01:00.0: reg 0x10: [mem 0x00000000-0x0000ffff]
[14696.184904] pci 0000:01:00.0: PME# supported from D0 D3hot
[14696.185322] pci 0000:01:00.0: BAR 0: assigned [mem 0xf8000000-0xf800ffff]
[14696.185483] rt2800pci 0000:01:00.0: enabling device (0000 -> 0002)
[14696.185769] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 2872, rev 0200 detected
[14696.206390] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 0003 detected
[14696.291978] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[14696.379112] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[14696.389887] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34

---

### Post by tgalati4 on 2015-08-06
It's possible that the Ralink firmware that is loaded into your wireless chipset rejects AP's from a country that is not coded into your region.  That would explain why you see the various AP's for a few seconds and then the card shuts down.

> Region: Europe/London (based on set time zone)

country 00: DFS-UNSET

You would need to capture some more data using various wireless tools.

```
man wireless
```

Your wireless card is probably in "n" mode.  Try forcing it to "g" mode when in public places.  It could be a simple matter that your wireless card works well as an "n" device at home, but not so well in switching to "g" mode when out and about.  That is also consistent with seeing AP's for a few seconds and then having them disappear.

---

### Post by Hadaka on 2015-08-06
Hi , to set your current country code  Europe/London, please do.
Copy an paste to avoid error...
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
```
to view other countries codes...
```
cat  /usr/share/zoneinfo/zone.tab
```

---

### Post by superian on 2015-08-07
Thanks. I've tried those two lines and it still doesn't work.

I am not entirely sure that this card does 'n' - in Denmark, I could (for those few seconds) see the 2.4GHz 'g' signal from the flat's router, but never the 5GHz 'n' one.

---

### Post by superian on 2015-08-08
> **superian said:**
> I'm using Lubuntu 15.04 on an EeePC 901. Using the home wireless network is fine, but two times in two different places recently, it has seen all the networks for a few seconds and then decided it cannot see any.

I'm now back home and it is, again, working perfectly...

---

