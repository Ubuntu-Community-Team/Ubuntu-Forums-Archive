---
title: "ISA network card"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by christooss on 2006-07-19
I have found old network card. And now I would like to install it. Its ISA (you know one before PCI)

Thanks for the anwsers

---

### Post by mogelhead on 2006-07-20
For a while I had my old 486 as a router/firewall with two 3com ISA network cards and debian installed. I remember there was trouble setting it up, but it worked.

What brand and model is it?

---

### Post by az on 2006-07-20
You may have to load the kernel module by hand, maybe not.  It depends.  Some ISA hardware is not safely scanned by the kernel so is not autodetected.

Stick it in and boot.

If you need to load the module, you do this:

sudo modprobe 3c509
(3c509 is the kernel module for an EtherlinkIII 3Com ISA network card)

and if then you get an eth0 device to configure, you are successful.  Add the module to /etc/modules so that it loads every time you boot

sudo nano /etc/modules

and all the word 3c509 at the end of the file.  Save and exit.

You will have to know the kind of card it is to find the right module to load.  Look at the card and find the kind of card it is or the identification on the chip.  Google it with the word linux and you should find something which gives you a clue.

---

