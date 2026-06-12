---
title: "Verizon aircard and new ubantu linux"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by rallphpam on 2007-07-21
I have the latest addition of Ubantu and would like to use my Verizon Sierra 595 air card with it.  How can I get it to work?

---

### Post by Floppyjoe on 2007-07-21
You will have to determine the chipset of the card by using the following commands from the terminal:
To open a terminal click on applications/accessories/terminal.
For a USB device:
```
lsusb
```
and for a PCI device:
```
lspci
```
Find the line or lines which apply to your card and do a search on Ubuntu Forums for a method to install them.

---

