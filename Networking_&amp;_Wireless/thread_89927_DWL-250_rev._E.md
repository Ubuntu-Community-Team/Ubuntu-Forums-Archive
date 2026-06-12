---
title: "DWL-250 rev. E"
date: 2005-11-13
forum: Networking &amp; Wireless
---

### Post by sedition on 2005-11-13
Hi all,

I'm setting up a box to play media gateway for my house and I decided to go with Ubuntu (5.10, Breezy Badger) as the OS. I have a D-Link DWL-250 rev. E1 laying aroung and figured I could use it to put the box on my network.
I've followed the following wiki ([https://wiki.ubuntu.com/DLinkDWL520E1](https://wiki.ubuntu.com/DLinkDWL520E1)) to the "t" (even had to pull down gcc 3.4 because of problems during hostap compilation). I rebooted and used System -> Administration -> Network Settings to add in my ESSID and key, per the wiki's instructions. Now the wlan0 will not come up anymore after reboot. It has completely disappeared from the Network Settings, but appears in lspci.

Any help would be greatly appreciated, thanks in advance.



--------------------------------------------------------------
/etc/network/interfaces:
--------------------------------------------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep

# The primary network interface
iface eth0 inet dhcp

auto eth0

iface wlan0 inet dhcp
        hostname your.hostname.com
        fw_primary /etc/firmware/pm010102.hex
        fw_secondary /etc/firmware/rf010803.hex
        wireless_mode managed
        wireless-essid Wireless
        wireless-key s:XXXXXXXXXXXXX

auto wlan0



--------------------------------------------------------------
sudo iwlist wlan0 scan
--------------------------------------------------------------
wlan0     Interface doesn't support scanning.



--------------------------------------------------------------
iwconfig
--------------------------------------------------------------
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device wifi0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wifi0     IEEE 802.11-DS  Mode:Managed

wlan0     no wireless extensions.

sit0      no wireless extensions.

---

### Post by greenwom on 2006-06-18
Funny thing, I just had the same problems in Dapper.  I tried adding a 
/etc/hotplug/blacklist file with the orionco modules in it /// This was referenced in the Wiki and I seem to remember Breezy having it but the blacklist text file was missing there was a blacklist.d directory.  I'm guessing that this is normal either way it didn't work

How do we get the system to see the card and assign it a network name (wlan0)??

---

