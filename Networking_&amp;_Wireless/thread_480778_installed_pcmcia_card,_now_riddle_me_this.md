---
title: "installed pcmcia card, now riddle me this"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by Sylar_7 on 2007-06-21
OK I got a pcmcia card, uninstalled ndiswrapper drivers, and it recognized the card.
Its a Cisco card and I've heard 100% compatability out of the box from everyone i talk to.

But it says it has the same chipset as my  old internal wireless card.
My internal card is disabled in the BIOS, but it is showing up in neworkmanager and the entries for the two cards look identical.
I can't connect on either one...

so my question to begin I guess is:

How do I make ubuntu not recognize my old card?

and then

how do i make it use my pcmcia card?

i hope someone can help...
thanks!

---

### Post by tturrisi on 2007-06-21
what chipset?
and the interfaces can be renamed so you can distinguish them, but first let's handle the correct drivers.

---

### Post by Sylar_7 on 2007-06-21
They both say Atheros AR5212 802.11abg NIC.

I have the windows drivers and can use ndiswrapper to make the internal card work.
When I put the pcmcia card in when the ath_pci driver is blacklisted the computer freezes.
When I put the card in and ath_pci is not blacklisted and the ndiswrapper isn't being used, the two interfaces show up, even if I ifdown ath0 (the internal card) and disable the internal card in the BIOS...

---

### Post by tturrisi on 2007-06-21
You don't need ndiswrapper, get rid of it completely & use the madwifi drivers.
The devices should show up as ath0 & ath1.
I don't use network-manager becauise I think it's buggy and it's easier to just use net-admin or manually config  wifi.  I have 2 atheros cards and they both work well.

Turn the minipci device ON via the bios.
Unistall ndiswrapper via Synaptic (choose remove completely).
Uninstall network-manager via Synaptic. (choose remove completely)
Uninstall restricted-modules madwifi.
Verify the ath is not blacklisted.
Remove the pcmcia card.
Connect by wire.
Open a root terminal and do:
```
ifconfig ath0 down
ifconfig wifi0 down
rmmod wlan_wep ath_rate_sample ath_rate_onoe ath_pci wlan ath_hal ath_rate_amrr 2>/dev/null
cd /usr/src
apt-get install build-essential
apt-get install linux-headers-`uname -r`
apt-get install subversion
svn checkout http://svn.madwifi.org/trunk/ madwifi-ng
wget http://patches.aircrack-ng.org/madwifi-ng-r2277.patch
cd madwifi-ng
patch -Np1 -i ../madwifi-ng-r2277.patch
make
make install
depmod -ae
modprobe ath_pci
```
Stick in the pcmcia card & do:
iwconfig
You should see ath0 & ath1
If your laptop has a ON-OFF switch for onboard wifi then see this:
[http://madwifi.org/wiki/UserDocs/MiniPCI](http://madwifi.org/wiki/UserDocs/MiniPCI)

---

### Post by Sylar_7 on 2007-06-21
how do I uninstall restricted-modules madwifi?
I see how to not enable them in the restricted drivers app, but it still says in use even after a restart.

Nevermind, I will just uninstall the whole package and worry about the nvidia driver later

---

### Post by Sylar_7 on 2007-06-21
When I do


```
modprobe ath_pci
```

I get

```
FATAL: Error inserting ath_pci (/lib/modules/2.6.20-16-generic/net/ath_pci.ko): 
Unknown symbol in module, or unknown parameter (see dmesg)
```

EDIT

Also, I rebooted and now X wont start because the nvidia driver is missing... =/

---

