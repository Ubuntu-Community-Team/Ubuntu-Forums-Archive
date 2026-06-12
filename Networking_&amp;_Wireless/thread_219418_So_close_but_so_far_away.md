---
title: "So close but so far away"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by OctopusTwo on 2006-07-19
Hello.
So a friend and I are trying to connect my WPN111 Wireless adapter to the Internet using the latest version of Ubuntu.  We have installed the drivers, the .inf file and ndiswrapper compiler  We confirmed this by using the ndiswrapper -1 and “hardware present” was displayed in terminal. 

This is the Network interface in the etc/network/ directory
auto lo
iface lo inet loopback

mapping hotplug
	script grep
	map eth0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless_keymode open
wireless_key = "my WEP key"
wireless_mode managed
wireless_essid = "BINGEN"
wireless_nick = "jacob"

auto wlan0

Any other questions please ask.  Thanks for any or all of your help on this issue.  We are at a loss.  Thanks again.

---

### Post by wieman01 on 2006-07-20
Try this (no underscore, no apostrophe, no equal-sign):

auto wlan0
face wlan0 inet dhcp
  wireless-essid your_essid_id
  wireless-key your_WEP_key

That should do it. I need 4 lines to configure my wireless card using WEP & ndiswrapper.

Hope this brings you even closer.

---

### Post by krazyd on 2006-07-20
Have you tried network manager?

---

### Post by OctopusTwo on 2006-07-20
autowlan0
facewlan0inetdhcp
wireless_essid = BINGEN
wireless_key = key...

This is how I set it up now.  Is this correct.  How would in ensure everything is set up correct?  How do I ensure I set up the wrapper thing up correctly?
How do I configure wireless networks in the network manager if no wireless networks appear.  Currently I see ehernet connection and modem connection. 
Or does any one know of a guide to install Atheros chipsets perhaps that would just be easier.
Thanks once again for your help.

---

