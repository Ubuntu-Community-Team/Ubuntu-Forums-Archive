---
title: "What to do if lspci doesn't see my card?"
date: 2005-07-23
forum: Networking &amp; Wireless
---

### Post by otakuj462 on 2005-07-23
Hi, I'm currently trying to configure an old desktop PC of mine to act as a wireless router. I have a D-Link wireless card plugged into one PCI slot which is configured and working fine. I also have a 3Com 3c905c ethernet card plugged into the other PCI slot, and the computer fails to detect it at all. lspci returns all other cards plugged into the motherboard, but not the 3Com chip. I've tried doing modprobe 3c59x, and, indeed, lsmod | grep 3c59x returns:
3c59x     37160  0

 What is the next logical step to get the system to see my card?

-Jake

---

### Post by scoon on 2005-07-23
Hey there, 

It has been my experience that if the kernel (lspci) can't "see" the card then one of three things is the problem:

1. The card just won't work w/ linux
2. The card is not fully inserted into its slot.
3. The card and/or slot is AFU.

regards, 

scoon

---

### Post by otakuj462 on 2005-07-24
What do you mean by AFU? How could I test this?

-Jake

---

### Post by joevandyk on 2005-07-24
Hehe.  "All Fooked Up" is I think what he means by AFU.

---

### Post by scoon on 2005-07-24
Hey there, 

That is correct.  All F*kc'd up.

regards, 

scoon

---

