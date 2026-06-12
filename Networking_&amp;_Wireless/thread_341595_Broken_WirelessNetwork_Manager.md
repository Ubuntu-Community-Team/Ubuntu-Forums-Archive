---
title: "Broken Wireless/Network Manager"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by Mike-97470 on 2007-01-18
Well, I installed Ubuntu 6.10 on my laptop from a CD and it worked great!!

After updating the upgrade, I installed the Network Manager and everything worked great!  My wireless LAN worked great too (w/ WPA).  And the persistence of the wireless connection was much better than using W$$.  Yea!

As I recall all I did to get it working was to enter some wireless info in System/Administration/Networking and type a password into the KEYRING (huh?).  And the little double-monitor nm-applet chased it's tail in a little green circle and the laptop connected.

But then it stopped working and I don't know why, so I checked into the forums . . . 
1. I deleted everything in /etc/networking/interfaces except--
auto lo
iface lo inet loopback
2. I also deleted the nm-applet key in the Keyring just for good measure.  (It just seemed redundant to me!)
3. That's it, I didn't do anything else!

So now:
1. The nm-applet only indicates a wired connection which works fine.
2. I've un-installed the keyring and network manager to no avail--the network manager reports that it can't "get in-touch with" whatever (resources).  That's pretty obvious!
3. System/Administration/Networking shows my Wireless connection exactly as I set it up, and when I un-check and re-check the connection a little window/dialog box pops up saying "Activating network interface".  But other than that nothing happens.
4. I installed Wifi Radar and naturally it sees a bunch of Wifi nets including mine.  It even indicates that my laptop is connected!!!  (Huh?)

So please let me know what I need to do to re-enable the Network Manager or otherwise fix.

Thanks,
Mike

---

### Post by teaker1s on 2007-01-20
uninstall wifi radar and install
network-manager-gnome


now on your desktop panel you want to click system administration networking

it's important to make sure that devices show unconfigured so network-manager-gnome can control them. Shutdown and remove ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in passphrase or network key
_

---

### Post by Mike-97470 on 2007-01-21
Thanks teaker1s,
Ok, everything seems to be working fine now . . . here's what I did (ymmv):
1,  Yes, System/Administraton/Networking should show a wireless connection if the driver is installed, but IT MUST NOT BE CONFIGURED!!!  Surprise!  This is really a design "feature" that could be improved.
2.  In order for a wired connection to work, I'm pretty sure that it must be enabled and configured in System/Administration/Networking.
3.  I did reinstall the 3 Network Manager packages and deleted the nm-applet Keyring key.  nm-applet seems to reinitialize everything when the system reboots.
4.  I also deleted everything in /etc/network/ exceot:
auto lo
iface lo inet loopback
5.  With the wireless interface working, /etc/network/ looks like:
auto lo
iface lo inet loopback

iface eth0 inet dhcp



auto eth0

with just the loopback and wired entries, it does not have a wireless entry!!

Finally, just for the record:  I'm using the Intel 2200bg in a T-30 IBM Thinkpad--the 2200bg has a Linux driver.

Whew!

---

