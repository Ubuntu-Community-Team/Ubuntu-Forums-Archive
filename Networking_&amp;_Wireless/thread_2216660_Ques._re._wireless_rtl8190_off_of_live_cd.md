---
title: "Ques. re. wireless rtl8190 off of live cd"
date: 2014-04-13
forum: Networking &amp; Wireless
---

### Post by steelpitt on 2014-04-13
I have an older pc, with windows xp.  I want to install linux, rather than get a new computer.  I want to run some features off a live cd before running any install, so here are my questions.

1. can i set up my wireless nic while running ubuntu off of a live cd, or do i have to install ubuntu to set up wireless nic?
1A. if I CAN set up wireless nic on live cd, How, searched through google and forums, and can't seem to find simple step by step guide

2.  my current set up is this:  desktop is windows xp , wireless nic, usb plugged in printer.  printer is shared in xp , and other latptops and tablets see printer and print wirelessly to it(printer does not have wifi abalities)  I would like to install linux on the desktop where the printer is hooked up to , and have printer shared , allowing vista and windows 7 laptops to print to printer hooked up to linux desktop, all running on same network.

I would like to run these two features before doing install and later finding out I can't.
also I can run a wired connection(for set up to desktop run wire across room on floor) but can not run wire and keep it perminently.

sorry if newb question, but i have searched,  Hopefully questions are clear. thanks

---

### Post by praseodym on 2014-04-13
Hi,

this device is "tricky", if it works with the native Linux driver which is part of the kernel you can setup the connection via network-manager:

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

Picture (in German):

[http://media.cdn.ubuntu-de.org/wiki/attachments/12/52/nm-einstellungen-wireless.png](http://media.cdn.ubuntu-de.org/wiki/attachments/12/52/nm-einstellungen-wireless.png)

Check with Live-CD the terminal outputs (CTRL+ALT+T) of
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
```

For the printer:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

You should be able to share it with Live-CD, too. What kind of computer and printer are they?

---

