---
title: "Belkin Wireless G Desktop Card Help"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by James765 on 2008-07-08
I've only been using Ubuntu for a couple of hours now and Im lost.

I'm trying to get online using a Belkin Wireless G Desktop Card (Model: F5D7000uk Ver. 7021uk) but have no idea what Im doing.

Im running Ubuntu 8.04.1 through Windows XP and have no wired connection.

Can anyone help me please?

---

### Post by pytheas22 on 2008-07-08
If your card is internal, please run this command:
```

lspci
```

I won't ask you to copy and paste the whole output here, since it would be difficult without a wired connection, but please at least post the line in the lspci output that relates to your wireless card.  It should be easy enough to spot the line; it will probably begin with "Ethernet controller" or "Network controller" or something like that, and may mention Belkin.  Please copy the full line here.

If it's a USB stick, please run:
```

lsusb
```

and again, post the line relating to your wireless card.

This information will let us know which chipset your card has, which is the important thing--the manufacturer and model don't mean much because the guts of the cards can change even though the name on the box stays the same.

---

