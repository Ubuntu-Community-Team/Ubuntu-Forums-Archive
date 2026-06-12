---
title: "Wireless Connection DNS Problem"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by TomFalc on 2007-07-27
I have been running Edgy on this laptop for a while, and had everything working well.  I rebuilt it to get a clean fresh installation of Feisty.  The installation is using the madwifi drivers for the Atheros wireless network.  I have installed wpa_supplicant as my home network is secured using WPA.

When I boot up without the wired connection, the wireless connection seems to work, but DNS doesn't.  I can ping sites if I use the IP Address, but not the name, most of the time. Occasionally, it works properly.

When it doesn't I need to restart the wireless interface using ifdown followed by ifup.  Normally, this fixes the DNS issue.

Can anyone suggest a cause for this behavior so I can correct it?

Thanks,

Tom

---

### Post by moore.bryan on 2007-07-27
*have you setup dns server addresses on your router?*

---

### Post by TomFalc on 2007-07-27
Sorry, I should have said.  I do not have to adjust the router at all.  The only change I have to make is to stop and restart the ath0 interface on the laptop.

If I use a wired connection, I have no problem.  The eth0 interface is up, but bringing it down does not fix the problem.

Cheers,

Tom

---

### Post by moore.bryan on 2007-07-27
[I]i'm trying to remember how i finally got madwifi and atheros working on my thinkpad, but i'm really not sure... out of a thousand commands, one worked... i guess.  :-)

what do your /etc/modules and /etc/network/interfaces files look like?
[/I]

---

### Post by TomFalc on 2007-07-27
/etc/modules only contains:

[FONT="Courier New"]# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2[/FONT]

/etc/network/interfaces contains:

[FONT="Courier New"]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp
pre-up wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

auto wlan0
iface wlan0 inet dhcp
[/FONT]

Is there an option which closes the interface if it isn't connected?

---

### Post by moore.bryan on 2007-07-27
*try adding pci_ath to your /etc/modules file.  according to madwifi, that's supposed to be loaded.  it didn't work on my machine, but it might work on yours.  you also may want to check and make sure everything in the /etc/wpa_supplicant.conf file is correct.  do you use network-manager(-gnome)?  i was finally able to get everything working at boot using [wicd]("http://www.wicd.org/"); i think it's in the repos.*

---

### Post by TomFalc on 2007-07-27
Adding ath_pci into /etc/modules seems to have fixed it, although this may be one of the odd occasions when it works anyway.

All the same, its a pretty impressive coincidence, so I'll assume it is fixed for now.

Thanks for all of your help.

Tom

---

### Post by moore.bryan on 2007-07-27
*just glad you got it working... if it is one of the "odd occasions," just repost and we can try to work it out.*

---

