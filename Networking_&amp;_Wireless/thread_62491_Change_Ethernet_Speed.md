---
title: "Change Ethernet Speed"
date: 2005-09-04
forum: Networking &amp; Wireless
---

### Post by X5-655 on 2005-09-04
I just setup my first ubuntu computer (a mini PC for the living room computer for everyone to use), and I have one question..

How can I change the ethernet speed?

The 3COM card in this system keeps using 100 megabits as the card can do it, and the hub can do it, but since the cable is actually too long, I am required to use 10 megabits, otherwise the connection is HORRIBLY slow.

Is there anyway to set the ethernet speed to be 10 megabits?  Or will I have to insert a 10 megabit ethernet card?

---

### Post by evilghost on 2005-09-04
There is a way to force it to use 10Mbit, but I'll be darned if I can't remember it.  Let me research and I'll respond.

---

### Post by evilghost on 2005-09-04
Ok, you can try this, but not all drivers support it, so it may not work:

sudo ifconfig ethX media 10BaseT

If it doesn't work let me know and I'll continue to research.

---

### Post by X5-655 on 2005-09-04
[QUOTE=evilghost]Ok, you can try this, but not all drivers support it, so it may not work:

sudo ifconfig ethX media 10BaseT

If it doesn't work let me know and I'll continue to research.[/QUOTE]
i will give that a shot in the morning, im going to sleep right now..

---

