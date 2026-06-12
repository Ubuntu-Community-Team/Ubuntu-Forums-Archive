---
title: "No Internet Connection after Installing 9.04"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by jeff_phil on 2009-08-05
Hi there!

I just finished installing 9.04 from 8.10. I checked for internet connection but there was none. Also, when I booted to my WinXP, the network adaptor is gone. I do not know what is going on. A help is really appreciated.

---

### Post by LewRockwell on 2009-08-05
how did that network run when you tested it out with the 9.04 Jaunty LiveCD test-session?

.

---

### Post by SuaSwe on 2009-08-05
Do you have the ethernet adapter listed under Device Manager? (Start -> right-click on My Computer -> Properties -> Hardware -> Device Manager) Check if it has a red cross or yellow question mark over it.

Also, do you have your ethernet connection (probably called eth0) listed when you go into Terminal in Ubuntu and do

> ifconfig

?

If your ethernet card is onboard it may also have become disabled in the BIOS somehow; have you checked?

---

