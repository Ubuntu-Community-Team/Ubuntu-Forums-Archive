---
title: "Problems with WMP54G"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by s1k3st on 2006-08-14
I'm having some trouble getting my wireless card to work.  I'm pretty sure I have ndiswrapper set up right, because it says the drivers and hardware are present.  The problem is when I try to activate the connection it does nothing.  It will say it is activated till I close the window, then when I reopen it it says that it's not activated.  I'm really new to linux so any step by step instructions would be awesome.

---

### Post by chrisbenson on 2006-08-14
No answer here, but I'm having the exact same problem with the exact same Linksys Wireless-G PCI card.  It appears to activate, but doesn't - although you have to go back into networking to verify that.

---

### Post by s1k3st on 2006-08-15
After hours of searching I finally found a fix for this.  Simply add "blacklist bcm43xx" to /etc/modprobe.d/blacklist  I'm not sure it will work for you, but it worked for me so it's worth a try.

---

### Post by bionnaki on 2006-08-15
what driver does your wmp54g use? if they use the rt2500, you dont need ndsiwrapper. ndiswrapper sucks.

---

