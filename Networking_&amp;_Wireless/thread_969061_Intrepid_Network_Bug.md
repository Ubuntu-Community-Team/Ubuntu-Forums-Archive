---
title: "Intrepid Network Bug"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by inkrypted on 2008-11-03
If like me you upgraded to Intrepid and then found that you could not edit your network or could no longer use static settings because they kept defaulting to dhcp upon reboot. Here is what I did to resolve my issues until they get this figured out. I simply installed another network manager and I must say I am impressed with this one. Here is the link.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by nesh8 on 2008-11-03
hi guys,

wicd is works great for me...... :D ( thx alot )

no more rebooting after my lappy sleeps...

direct download from the site works....

---

### Post by 8oluf7 on 2008-11-07
Wicd worked for me too!

I did a fresh install of Intrepid on an IBM ThinkPad T40 and everything was fine until I tried to fire up the wireless networking with encryption and the various lock-downs I use. After much searching of the forums and trial-and-error I got the thing to work - but it kept asking me for the encryption key every time I started the machine. Not the sort of thing one wants to give to one's mother-in-law, who has volunteered to be switched to Linux at a very advanced age. 

Part of my difficulty was that most of the forum material referred to the Intel or Cisco WiFi cards - but I have an Atheros AR5212!

Anyway, Wicd did the business. Incidentally, they don't seem to have an Intrepid repo set up yet, so I downloaded the non-distro-specific file and Gdebi did the business (after I'd removed network manager which it pointed out was a conflict).

Many thanks for the pointer.

---

### Post by inkrypted on 2008-11-09
I am glad this is working for more people than just me it really frustrated me when I upgraded and this happened but at least there was a solution.:)

---

