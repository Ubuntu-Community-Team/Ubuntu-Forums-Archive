---
title: "Hotplugging ethernet interfaces (wired &amp; wireless)"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by abrichr on 2007-08-20
Both my wired and wireless connections work, but only if they are connected while the computer is starting up.

if I boot up with no Ethernet cable plugged in to the wired interface, the device is visible in ifconfig, but dhclient can't acquire an address after connecting a cable.

If the wireless switch is turned off while booting up, and I turn it on after having booted up, it is similarly visible in ifconfig, and I can even scan networks using the command iwlist eth1 scan.  dhclient, however, is unable to acquire an address.

This is quite annoying when I boot up having forgotten to first turn on the switch, or plug in the ethernet cable, and then have to reboot in order to connect.  Is there any way to force the drivers to acquire an IP, or reload them completely?

---

