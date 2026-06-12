---
title: "PCI Wireless, WPA, and stuff..."
date: 2005-05-17
forum: Networking &amp; Wireless
---

### Post by Stealth on 2005-05-17
I reading through the wiki and stuff, and was wondering if Ubuntu supported any card and WPA encryption out of the box? Apparently its all WEP stuff, and you need to install a package for WPA.

I plan on building a desktop, but don't want to shell out for Windows XP just to have wireless working. Any PCI cards out there, 802.11g, with WPA, that are very easy/known to setup/work?

---

### Post by zencoder on 2005-05-17
The _wpa-supplicant_ deb package is not currently in the seeds for Hoary.  It has been proposed to be added as a Supported seed, but is not yet official, afaik.

[http://www.ubuntulinux.org/wiki/SupportedSeedProposals](http://www.ubuntulinux.org/wiki/SupportedSeedProposals)

That being said, you can get it installed in moments.  Add a universal repository, and from a root shell enter **apt-get install wpasupplicant**


/* Edit */

Sorry, realised there wasn't a lot of answer to my original post.

Stealth, I've found Ubuntu to support every single wireless card I have, out of the box.  No exceptions, no caveats.  WPA is a different story, see my info above.  I am an avid fan of Ubuntu at the moment, due to many factors (ease of setup, convenience, thouroughness of the initial system you get, etc.), but the biggest is the out-of-the-box hardware support.

---

### Post by Calgarian on 2005-05-18
Zencoder:

I have a desktop machine based on an Intel motherboard. Right now I'm wired on the net in my living room (rental partment with brick walls) so I need to go wireless. I'm at Hoary 5.04 with all current updates applied. My ISP is high speed cable. Can you recommend a card to install in my desktop and a router/hub to go with it? By the way, my wife is just getting a MiniMac with the airport card and it would be nice to have both work off the same router/hub.

---

### Post by Stealth on 2005-05-18
Which network cards (that support g and WPA) have you tried that work?

---

### Post by Calgarian on 2005-05-19
I haven't tried anything yet. As of now I've got a wired card (3Com 3c905C). The MiniMac has been ordered with an Airport Extreme builtin. I thought I 'd ask before I bothered trying anything at all.

---

### Post by Stealth on 2005-05-19
Question was really for zencoder ;)

---

### Post by anders.ostling on 2005-05-22
Well, after a few hours of struggling with helpful network admins, I finally made my ipw2100 card work with WPA (actually Cisco LEAP and dynamic WEP). The pre-authentication was done by Cisco ACS with help from an AD domain controller, and then I got 128 bit wep keys from the AP. Had to do several manual steps though, hopefully it will all be integrated someday.

1. Prepare the AP (set ESS id and a dummy key in order to have the association to work)
2. Run xsupplicant (not wpa_supplicant) with the -W command parameter. This would read the xsupplicant.conf parameters and do the pre-authentication and then the wep key exchange.
3. Run dhclient manually in order to have an IP adress

Note that this was done with the latest PRE version of xsupplicant. I could not get the Hoary deb package to work at all!

If anyone need help, dont hesitate to contact me

Anders

---

