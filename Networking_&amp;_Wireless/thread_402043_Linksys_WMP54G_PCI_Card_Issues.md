---
title: "Linksys WMP54G PCI Card Issues"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by Forgott3n on 2007-04-05
Using:
Ubuntu 6.10 Edgy Eft -- Clean install
Linksys WMP54G PCI Card
(Note: I had to set acpi=off in GRUB and LiveCD to get Ubuntu to boot)
Linksys Router WRT54G v.5 (DD-WRT Firmware Installed) with WPA-PSK TKIP+AES wireless encryption.

I went into Network-Settings to enable the wireless device (ra0) and give it its credentials. I put everything in correctly and went to ping my gateway or google but no luck.

I do not know what to do.

Thank you for helping!

---

### Post by MeeMaw on 2007-04-05
This post is helpful
[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

especially the posts about editing your /etc/Wireless/RT61STA/rt61sta.dat file

(sometimes the Network-Settings doesn't keep all the info and you can edit it by adding the correct information in gedit. Just do "sudo gedit /etc/Wireless/RT61STA/rt61sta.dat" and put in the ESSID and encryption key, etc.)

Good luck!

---

### Post by Forgott3n on 2007-04-05
My card uses the RT2500 driver, but I kinda bastardized that post to suit my own needs. So far I cannot get it to work, still.

I am utterly confused. Why does Ubuntu's site claim that this works out of box?

---

### Post by j-strap2 on 2007-04-07
I got the very same card working in kubuntu edgy. It took some fiddling and I have forgotten exactly what I did. Basically, I used ndiswrapper and I also had to stop the bcm43xx module from being automatically loaded by adding the line 'blacklist bcm43xx' to the file /etc/modprobe.d/blacklist.

When I had the wireless connection working, I enabled encryption using the wicd package from here: [http://ubuntuforums.org/showthread.php?t=299462](http://ubuntuforums.org/showthread.php?t=299462)

I cannot recommend wicd too highly after all the trouble I have had with network-manager and related packages. wicd just works.

---

### Post by Forgott3n on 2007-04-07
> **j-strap2 said:**
> I got the very same card working in kubuntu edgy. It took some fiddling and I have forgotten exactly what I did. Basically, I used ndiswrapper and I also had to stop the bcm43xx module from being automatically loaded by adding the line 'blacklist bcm43xx' to the file /etc/modprobe.d/blacklist.

When I had the wireless connection working, I enabled encryption using the wicd package from here: [http://ubuntuforums.org/showthread.php?t=299462](http://ubuntuforums.org/showthread.php?t=299462)

I cannot recommend wicd too highly after all the trouble I have had with network-manager and related packages. wicd just works.

Thank you for helping me. I am just curious, for ndiswrapper what driver did you install? rt2500 or bcm43xx?

I just installed the rt2500 and then ran "ndiswrapper -d 1814:0201 rt2500"

and now I installed wicd via .deb file from my thumbdrive...

I tried to connect using the wicd's tray-edgy.py but with no avail. I tried the the 'wext' and 'ndiswrapper' under preferences in the gui.

Did I miss anything?

[EDIT] I also tried connecting to an Open/Unsecured wireless network. That did not work either...

---

