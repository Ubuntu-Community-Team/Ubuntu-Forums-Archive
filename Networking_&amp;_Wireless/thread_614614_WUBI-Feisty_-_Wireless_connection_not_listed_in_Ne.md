---
title: "WUBI-Feisty - Wireless connection not listed in Network manager"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by yosibeck on 2007-11-16
I am still somewhat unfamiliar with Linux. Sorry.
I have a new Toshiba A200 laptop with Vista Home Premium pre-installed (sorry about that too...)

I have installed Feisty 7.04 with WUBI. (Since I'm new to this I didn't want a real install yet, and WUBI for Gutsy is still in alpha).

The problem is that a wireless connection is not at all mentioned under the Network Manager.  (Only "wired connection" and "modem connection" appear.
What to do?

In Ubuntu, doing lspci in the terminal shows me the following entries:
[B]Network controller: Intel Corporation Unknown Device 4229 (rev61).
Ethernet controller: Realtek Semiconductor Co Ltd RTL8101E PCI Express Fast Ethernet controller (rev 01). [/B]

In Vista (where the wireless network works fine) I have the following entries in the Control Panel:
[B]Network adaptors:
Intel Wireless WIFI Link 4965AGN
Realtek RTL8101 Family PCI-E Fast Ethernet NIC (NDIS 6.0)[/B]

I don't know if this means anything but doing "iwconfig" tells me:
lo          no wireless extensions
eth0     no wireless extensions

/etc/network/interfaces has only this:
auto lo
iface lo inet loopback

dmesg tells me:
[5.248000] r8169 Gigabit Ethernet driver 2.2LK loaded

Assuming you can help me getting past this point and getting the wireless connection to appear in the Network Manager, maybe you can also help me along.
My router is 3COM using:
WPA settings:  WPA_PSK (no server)
WPA mode: WPA2
Encryption TKIP 
and of course the PSK key.

I would be very greatful for advice, at least get the thing to appear....
Yossi

---

### Post by madsmaddad on 2007-11-16
There was another post/stream about getting Encryption working in Feisty. after about 2 pages of stuff the guy commented that he had updated to Gutsy and got  WPA working. 

I have gone the same route and upgraded my Feisty to gutsy, but still cannot get WPA working. I have a 3COM router like you, with the same wireless config, and a 3com USB wireless connection. I know it is working because I am dual booted into XP to write this. 

There is another stream here where x wrote a guide on getting WPA working. so far it has failed for me. It involves using Supplicant. 

My experience to date is that none of the GUI programs interface with the configs correctly at the moment, and it's a CLI editing process. 

I'll let you know how I get on.

Peter M.

---

### Post by yosibeck on 2007-11-18
I"m not sure I'm up to the WPA problem yet.
I don't even have a Wireless **_option_** in the Network Manager.
By the results of the linux commands I posted above, it would seem Ubuntu doesn't even know I have a wireless option. So there isn't anything I can try to configure.
Anyone got any ideas as how to get this going?
I know people have wireless working in Feisty and even before, so it must be possible.
Thanks

---

