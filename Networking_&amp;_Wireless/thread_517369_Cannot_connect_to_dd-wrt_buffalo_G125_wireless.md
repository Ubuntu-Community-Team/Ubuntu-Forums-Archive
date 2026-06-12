---
title: "Cannot connect to dd-wrt buffalo G125 wireless"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by headlice on 2007-08-04
Hey all.

Ok, I just bought a Buffalo G-125 Airstation and had it set up with factory settings.  My laptop with XP connected just fine.  My desktop (the one I am working on now) has a wireless card in it and it connected just fine.  I even enabled WPA2-AES and both connected just fine.

Flashed the Buffalo G-125 with dd-wrt firmware with a date of 6/20/07.  This was setup as an unsecure wireless network.

Laptop connected just fine (XP).  This PC connected just fine.

When I enable WPA2-AES, Laptop (XP) connects just fine but this machine does not.  I switched between WPA2-TKIP, and WPA1 and nothing worked with this machine that I am working on.

Conclusions: factory settings on Buffalo router work for both PCs with security enabled and disabled.  dd-wrt unsecure works for both PCs as well.  Secure dd-wrt does not work for this PC.


This PC's specs:  Feisty with latest updates.  Ndiswrapper being used with a Zyxel 302-V3 wireless PCI card.  This is a PIII 700Mhz with 768MB RAM

---

### Post by headlice on 2007-08-04
Oh, I should let you know that I did (previous to this router) have a netgear router that also had WPA2-AES settings that I could connect to just fine as well.  This was factory settings and not modified.

Description of how it does not let me connect:

I click on my SSID and then it brings up a "Wireless Network Key Required" window.

I enter the password and it attempts to connect and then drops me and opens up the same window allowing me to enter the password yet again.  This goes on indefinitely....

---

### Post by headlice on 2007-08-04
bump....anyone?

---

### Post by wieman01 on 2007-08-07
So Feisty gives you the WPA(2) option using the Networking Applet as usual, right? And you could connect to your Netgear router just fine via WPA2, right?

---

### Post by headlice on 2007-08-10
Yes, that is correct.

---

### Post by headlice on 2007-08-14
K anyone have any ideas?

---

### Post by wieman01 on 2007-08-15
> **headlice said:**
> K anyone have any ideas?
It's hard to tell what settings are wrong, because according to what you have said in post #1, DD-WRT is the culprit. Perhaps attaching a few screen-shots makes a difference... e.g. security settings, wireless settings, etc.

---

### Post by Chrismartin76 on 2007-09-16
I have the same problem with my laptop, a Dell D610. I'm not using Ubuntu, though, but Win XP SP2. 
I'd like to revert to the Buffalo firmware but it doesn't seem possible.

---

### Post by lawr_rawr on 2007-10-04
I'm using the G125 with DD-WRT firmware and have no problems connecting to the wireless. My wireless card is a Ralink RT73. I am using WPA-Personal and TKIP. I've also connected my boyfriend's laptop, HP with Intel wifi.

---

### Post by kevdog on 2007-10-04
Which firmware version are you using?  I think the pre rc3 is the latest.

---

### Post by lawr_rawr on 2007-10-05
Heh, knew you'd ask that. Oddly enough I couldn't connect to the remote management page yesterday when I posted, but it's now working.

Firmware: DD-WRT v24 Beta (08/15/07) vpn

I am planning to upgrade in the next couple weeks to a version that supports multiple SSIDs. I am moving and won't have internet at home until next week... 

Let me know if you want any other settings.

---

### Post by jdids on 2007-10-17
If you're trying to connect to the router using AOSS, it won't work. 

Check out this link: [http://ubuntuforums.org/showthread.php?p=3551904#post3551904](http://ubuntuforums.org/showthread.php?p=3551904#post3551904)

It worked for me, and hopefully it will work for you!

---

