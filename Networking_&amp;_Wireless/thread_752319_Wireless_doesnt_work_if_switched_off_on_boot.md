---
title: "Wireless doesnt work if switched off on boot"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by marshall.robert on 2008-04-11
Hi all!

I have noticed that if i boot into Ubuntu with my wireless switched off, my wireless will not work atall, and i have to reboot.

Can anyone help to solve this matter?

many thanks  -rob

---

### Post by dstew on 2008-04-11
What type of wireless device is it? PCI or USB? Maybe your card needs to have the power on in order to be seen as present, and to be set up. If it is a PCI card, post the output of ```
lscpi
```done before and after you turn on the card, and after you reboot with the card turned on to see when it shows up. For a USB card, the command is ```
lsusb
```

---

### Post by TenPlus1 on 2008-04-11
Goto Terminal and type this:

sudo /etc/init.d/networking restart

It will restart your network and bring up your wireless...

---

### Post by marshall.robert on 2008-04-13
its an intel 3945 mobile wireless chip, so its in a laptop.

---

