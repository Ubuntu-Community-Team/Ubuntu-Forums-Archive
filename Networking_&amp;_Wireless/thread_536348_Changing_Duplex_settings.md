---
title: "Changing Duplex settings?"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by Aryding on 2007-08-27
I'm fairly certain that auto negotiation is on but is there a way that I can change that setting to 10mb's Full Duplex?  As well, how would I change it back?

FYI, my lan cable is too long for 100mb's Full Duplex.


Thanks!

---

### Post by Aryding on 2007-08-27
Bump... Thought this would be a fairly simple question.  Anyone?

---

### Post by spd106 on 2007-08-27
Most ethernet cards will work with the ethtool utility.

Run *sudo ethtool eth0* to get the capabilities of your card. The man page has all of the syntax details, though bear in mind that you will probably have to turn autonegotiation off to set a specific rate or duplex mode.

---

### Post by gigaferz on 2007-08-27
hello
i recomend mii-tool

[http://ubuntuforums.org/showthread.php?t=302403](http://ubuntuforums.org/showthread.php?t=302403)

ethtool did not work in any of the past ubuntus

---

