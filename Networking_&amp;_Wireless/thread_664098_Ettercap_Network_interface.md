---
title: "Ettercap Network interface"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by sniper9xm on 2008-01-10
I have recently installed ettercap, It cannot find my network interface. I know there are simillar threads but I havent found any useful help from it. 
 can any one help me with thsi problem?

---

### Post by chensamurai on 2008-04-12
I had the same problem. Here's how I "fixed" it. (I actually didn't fix anything, just started it incorrectly...)

Ettercap requires Root power so you must start it from a root terminal or with Sudo.

Either run the following command from a root terminal:
ettercap -G

or run this from a normal user terminal:
sudo ettercap -G

-bonne chance

---

