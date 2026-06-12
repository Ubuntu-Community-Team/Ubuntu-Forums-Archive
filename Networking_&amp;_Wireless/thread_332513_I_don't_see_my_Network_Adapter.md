---
title: "I don't see my Network Adapter"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by royksol on 2007-01-06
I'm beginner in Ubuntu
I can't connect to the Internet using Ubuntu. In networking I see only modem connection, but I have bandwidth connection. How to solve this problem?

---

### Post by Quillz on 2007-01-06
Are you using an ethernet cable or a wireless connection? If the latter, you might need to install ndiswrapper.

---

### Post by royksol on 2007-01-06
Ethernet

---

### Post by royksol on 2007-01-06
Ethernet cable connection

---

### Post by Quillz on 2007-01-06
Have you tried manually configured the eth1 connection?

---

### Post by kvonb on 2007-01-06
If your network card is not present in Menu->Sytem->Administration->Networking then you might have an unsupported network card and it will be a DRIVER problem.  Find out what brand/model it is and search these forums for that.

If you mean that you have a cable modem that connects to your USB port that is another story!  Again get the make and model then search for that.

Regards, KEv :)

---

### Post by royksol on 2007-01-06
No. But how to make it? Should I write something in Terminal?

---

### Post by royksol on 2007-01-06
I have Attansic L1 Gigabit Ethernet 10/100/  network adapter

---

### Post by kvonb on 2007-01-06
OK, click on: Menu->Sytem->Administration->Networking

and in the window that pops up, what is shown?

---

### Post by kvonb on 2007-01-06
I did a search for you, and it turns out that this network "card" is a problem!

You need to look on the driver CD that came with the mainboard, or go to [www.asus.com](www.asus.com) and search for the Linux driver for the Attansic chip.

When you've found the driver, this is how to install it:

[http://ubuntuforums.org/showthread.php?t=292838&highlight=Attansic](http://ubuntuforums.org/showthread.php?t=292838&highlight=Attansic)

Read post #2, it has instructions.

Alternatively, try and buy/acquire a cheap network card, look for Realtek/Intel/3com they are fully supported.

Regards, KEv :)

---

### Post by earobinson on 2007-01-13
Yup Im having this problem also

---

