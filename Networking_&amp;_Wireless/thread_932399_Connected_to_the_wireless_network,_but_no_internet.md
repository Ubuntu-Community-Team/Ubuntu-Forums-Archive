---
title: "Connected to the wireless network, but no internet"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by pugilist on 2008-09-28
tI'm using a Dell Inspiron 1501, with a Dell Wireless 1390 mini-PCI card. I have been to hell and back trying to make this card work correctly with Ubuntu.  I used bcm43xx-fwcutter, worked fine.  The problem is now that the card only wants to work in roaming mode, it will detect wireless networks and connect to them but can't use the internet and update manager for some reason.  I have been able to ping 4.2.2.2 and do a traceroute on 4.2.2.2 and have even been able to perform a whois on 4.2.2.2.  I've tried going into the Mozilla browser and disabling Ipv6 and that still hasnt fixed the problem.  I have tried everything in the bestt of my knowledge to get this to work.  It does work with ndiswrapper though, but I wanted to set my card up for monitor mode and ndiswrapper does not support that.  And for some reason I couldn't get the card to work with Ubuntu 8.04 so I downgraded back to 7.04 and it seems to be working besides the internet.   When I go to google in Mozilla it just sits there and hangs in Waiting for google.com. If someone could help me out it would be greatly appreciated.

---

### Post by pugilist on 2008-09-28
I've tried the troubleshooting and still not working.  Another wierd thing is with it.  Is that for some reason when it finds my ISPs dns servers: ping will work, whois, and traceroute will work but after I reboot they don't work anymore.  I have to remove the dns servers and pretty much reset the connection in order for them to work.

---

### Post by Rodney2 on 2008-09-28
I thought I had the same problem, perhaps you have the same one as I had.  I just did not have the "work off line" unchecked.  If you have your browser open, make sure that under "File" that the "work offline" is not checked.

---

