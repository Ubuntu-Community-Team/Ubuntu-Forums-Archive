---
title: "TP Link SC600 USB Adapter and Ubuntu ..."
date: 2019-01-02
forum: Networking &amp; Wireless
---

### Post by GameGuru on 2019-01-02
I recently moved and don't have the ability to run wire to my office so I have to go the wireless route.  I purchased a TP Link AC600 and when I plug it in I don't get any notification in Ubuntu Studio 18.10.  I downloaded the driver on my laptop and copied it to a thumb drive and put it on the desktop of my Linux machine but I am not sure what to do.

How can I easily get this adapter working with Ubuntu Studio 18.10 when I don't have internet on that PC?

---

### Post by wildmanne39 on 2019-01-02
Moved to networking and wireless.

---

### Post by praseodym on 2019-01-02
Please open a terminal with CTRL+ALT+T and show the output of

```
lsusb

```
to verify the chipset

---

### Post by GameGuru on 2019-01-02
Ok no internet connection so can't copy and paste here for you, what exactly am I looking for?

---

### Post by praseodym on 2019-01-02
Screenshot with cell phone? We are looking for the device ID

---

### Post by GameGuru on 2019-01-02
[IMG]http://i67.tinypic.com/2vt9sw2.jpg[/IMG]

---

### Post by GameGuru on 2019-01-02
I believe it's the Ralink Technology, Corp.

---

### Post by praseodym on 2019-01-02
Yes, it is. As I don't know about the driver it shipped with, so: Can you connect your smartphone via USB and establish a tethering connection? If yes, here is the installation instruction:

[https://ubuntuforums.org/showthread.php?t=2408678&page=2&p=13825311#post13825311](https://ubuntuforums.org/showthread.php?t=2408678&page=2&p=13825311#post13825311)

---

