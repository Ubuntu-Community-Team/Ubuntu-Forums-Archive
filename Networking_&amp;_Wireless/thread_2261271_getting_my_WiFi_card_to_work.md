---
title: "getting my WiFi card to work?"
date: 2015-01-17
forum: Networking &amp; Wireless
---

### Post by irongolem0982 on 2015-01-17
So I just installed lubuntu on my new pc via flashdrive. It has a wireless card and it does not show up with a connection or anything. In network connections it just shows a non connected Ethernet card. I don't have a way to connect it via anything but the WiFi card..  Please help

---

### Post by ajgreeny on 2015-01-17
Do you see a network icon in the panel, and what does it show if you click on it?

Let's also see the output of **lspci** and we'll work from there.

---

### Post by irongolem0982 on 2015-01-17
The network icon only shows Ethernet. Lspci | grep Network says: broadcom corporation bcm4318 air force one

---

### Post by irongolem0982 on 2015-01-17
Iwconfig shows: eth0 no wireless extensions, lo no wireless extensions

---

### Post by ajgreeny on 2015-01-18
Have a look at the sticky post at the top of this section of the forum.
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

