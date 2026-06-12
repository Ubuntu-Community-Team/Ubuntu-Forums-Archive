---
title: "Just installed Ubuntu, need help getting wireless to work"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by Kopachris on 2007-09-12
I just installed Edgy Eft (6.10, had the disk for a while) on my PowerBook G4.  My wireless card is a bcm4318.  The computer connected to the router runs Windows XP and has a Linksys router.  Here's the stuff I have in the Network Manager:

essid: poison (our network's name)
pass type: ASCII (we have no pass, though; use a MAC address filter)
config: DHCP (IP sould be in the 192.168.1.10x)
scan for resources is checked
DNSs:
74.211.15.210
74.211.15.211 (checked other computer's in our house for those)
Hosts:
127.0.0.1 localhost
127.0.0.0 Me

Did I do everything right?  I can't ping anything and I can't connect to the internet.

---

### Post by Vadi on 2007-09-12
See if this helps:

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

By the way, the current version of Ubuntu is 7.04 :)

---

### Post by Kopachris on 2007-09-13
Thanks, I'll try that.  I know Feisty Fawn is out, but I downloaded Edgy Eft about a year ago and it took a few hours to download and burn the disk.  I wanted to install Ubuntu now, not tomorrow.  I only have a few hours from getting home to going to bed.  Anyway, the wireless on the OSX side of my dual-boot harddrive still works fine.

---

### Post by Vadi on 2007-09-13
Yeah, that's because for it to work in Ubuntu, the company that made the card needs to tell Linux people how to operate the card.

They of course do that for mac and windows, probably getting a nice business out of it.

---

### Post by Kopachris on 2007-09-13
It didn't work.  Almost everything I've found requires me to be connected to teh internet in Ubuntu to get the stupid Airport Extreme card to work!  I need to find a bcm43xx driver to download that doesn't involve using Ubuntu to download it.  Know anywhere that might have the driver, other than a repository?

EDIT:  Found the driver, gonna try to install it manually, w/o ndiswrapper (ndiswrapper doesn't work for PowerPC, right?).
EDIT2: It worked!  Sorta.  I had internet (really slow, though), until I restarted it.

---

### Post by Kopachris on 2007-09-14
UPDATE:  Internet's working really well now.  I called my dad last night to tell him I'm going to bed (his truck's oil pump is broken, it's in the shop.  Good thing it's under warranty!) and told him that it worked for a little bit, then quit.  He suggested that I might have a firewall blocking our main computer, thus resulting in 100% packet loss.  This morning, I looked it up real quick in teh help, did a little masquerade command, and now it works!  I actually think it's faster than in Mac OSX!  I'm going to post an easy to use guide for other PowerPC users.  Then I'm going to update my computer.

P.S.  Sorry for DP.

---

### Post by Vadi on 2007-09-14
Glad it worked!

---

