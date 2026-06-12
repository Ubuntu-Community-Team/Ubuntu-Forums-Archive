---
title: "Problem with panda wireless adn ubuntu 12.04"
date: 2014-11-20
forum: Networking &amp; Wireless
---

### Post by markseger on 2014-11-20
I had been using my wireless card for close to a year and totally unrelated my sounds stopped working.  I had rebooted a couple of time with no luck and decided to update hipchat, similar to lync if you're not familiar with it, because it's audio conferencing wasn't working.  There was a LOT of stuff installed and was thinking I hadn't updated things in a log time so let it rip.  Bottom line is the machine came up fine and the sound now works, but my wireless isn't working any more.  I'm wondering if the kernel was rebuilt and/or if I need to reinstall the wireless driver.  Only thing is the only one I could find on the Panda site is for fedora and I'm not sure that's what I had installed.

Can anyone offer any suggestions on how to move forward?  I'll keep playing with google but am not optimistic.  If I do figure it out I will post what I did.

-mark

---

### Post by markseger on 2014-11-20
I probably should add this is 3.2.0-70-generic, from uname -r

if I run iwconfig it sees lo and etho but not ra0 which I'm configuring in /etc/network/interfaces like this, noting this used to work just fine

auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp
wpa-driver wext
wpa-ssid mywireless-name
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgt WPA-PSK
wpa-psk mypassword

then I run
service network-manager restart

and when I run ifconfig I see lo and eth0 but no ra0 as it used to when it was working

-mark

---

### Post by markseger on 2014-11-20
still digging but I did confirm this is a newer kernel because I have an initrd and grub dated today!
somewhere in looking around i saw a reference to needing to rebuild the driver if the kernel changes and I can't even find a driver for this anywhere other than one on the panda site named Fedora and I'm not sure if I should be messing with that or not.  still looking...
-mark

---

### Post by markseger on 2014-11-20
just got around to looking at syslog and see:

rt2800_init_eeprom: Error - Invalid RT chipset detected

huh?  remember this worked before
-mark

---

### Post by markseger on 2014-11-21
still no joy but from what I can tell is a regression was identified for the 3.7 kernel, which is what I'm running.  still haven't found a driver that might fix this though.
-mark

---

### Post by markseger on 2014-11-21
oops, my mistake.  the regression is for 3.7 and I'm running 3.2.0-70 so back to where i started ;(
-mark

---

