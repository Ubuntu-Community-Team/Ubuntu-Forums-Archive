---
title: "Gnome network-admin not using ifup/ifdown"
date: 2005-07-18
forum: Networking &amp; Wireless
---

### Post by Joshua Swink on 2005-07-18
Summary: How can I make network-admin use ifup/ifdown to control interfaces?

I have set up a wireless interface in /etc/network/interfaces so that a pre-up command turns on its transmitter and a post-down command turns it off, to save power. This works well when manually issuing ifup or ifdown. Here is the stanza:

[INDENT]iface eth0 inet dhcp
  pre-up echo "on" > /proc/acpi/wmi/WMID/wlan
  wireless-essid foo
  post-down echo "off" > /proc/acpi/wmi/WMID/wlan
[/INDENT]
Unfortunately, Gnome's network-admin doesn't seem to use ifup or ifdown. It jumps straight to some dhclient command trying to bring up the interface. That's not going to work, because the transmitter is off, and network-admin just hangs there with dhclient not receiving anything because it is not transmitting!

I find it surprising that network-admin will not simply issue ifup. Anyway how can I force it to do so? I could just use ifup/ifdown in a terminal, but I am trying to set this system up to be usable by others.

---

