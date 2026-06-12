---
title: "Attempting to connect with bluetooth FREEZES THE COMPUTER!?"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by AndrewZorn on 2008-05-03
I am following these instructions, trying to get my HTC Mogul to donate its data services to my laptop: [http://ubuntuforums.org/showpost.php?p=3779535&postcount=17](http://ubuntuforums.org/showpost.php?p=3779535&postcount=17)

Nothing fancy going on, just got to the steps where I make each device discoverable.

When I go to my phone and it sees my laptop, when I try to connect, I get a message on my phone saying it was unsuccessful.  I go back to my laptop...

**and it has frozen.  The Caps Lock and Num Lock blink.  Computer will not respond at all and requires a hard poweroff.  I've repeated this, it does the same thing every time.**

What on Earth could be causing this?  I really, really want to get the tether working, but this is just bizarre...

EDIT this only happens when you try to use a password.  When I skip the password step initially, things are fine.  But when I actually get to the part where they see each other and attempt to connect to the MAC address of the phone, then the phone 'sees' that it's being connected to and asks for a password.  You cannot skip it this time.  Put in a password, same flashing Caps and Num and FREEZING.

---

### Post by AndrewZorn on 2008-05-04
bump

---

### Post by AndrewZorn on 2008-05-08
bump
it's the night before a 21 day trip to the middle of nowhere, internet would be really nice... someone please tell me you've seen this before!

---

### Post by AndrewZorn on 2008-05-09
posting from PHONE...

please guys, any advice or anything?

---

### Post by winger1312 on 2008-05-23
I am having the EXACT same problem except when I try to connect my PDA.  It is definitely a bluetooth issue!

---

### Post by hoborocket on 2008-06-19
I had this happen twice, but now it doesn't. No idea what happened to fix it.

---

### Post by Langleyo on 2008-06-24
Looks like Bluetooth seems to be acting weird. The flashing lights apparently are to indicate a Kernel panic / total unexpected crash. I had this running some Btscanner applications on various dongles. I think it's some synchronisation issue between how Ubuntu and Bluetooth work together. Dunno if anyone has raised this to the coding guys?...I wouldn't know who to approach.

I got this Kernel dump when I ran my program in a terminal window. Hope it helps someone debug. If it does, I'd sure like to know what the exact problem is!


[http://ubuntuforums.org/album.php?albumid=257&pictureid=818](http://ubuntuforums.org/album.php?albumid=257&pictureid=818)

---

### Post by markthecarp on 2008-06-24
Same problem here. System completely locks up; flashing cap and numlock led's, keyboard unresponsive, mouse unresponsive. I've tried logging in from another local machine via ssh and running "tail -f /var/log/syslog" while attempting pairing. That did not prove helpful.

Ubuntu 8.04
Kensington dongle
LG VX9100

Pairing and file transfers work using openSuse11 Gnome. So I'm investigating by comparing the two.

-mark

P.S. There's an open bug report on Launchpad; I've added to it and encourage others having this problem to do the same.
[https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/234695]("https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/234695")

---

