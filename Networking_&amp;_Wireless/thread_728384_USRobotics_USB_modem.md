---
title: "USRobotics USB modem?"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by rburgan on 2008-03-18
US Robotics has a new USB modem coming out, that they indicate in advertising will work on Lunux. But the technical specs seem to indicate otherwise. A querry sent to them, brought the following response. Does this mean it will work under Ubuntu Gutsy, or Hardy, for that matter?

[[B]]Thank you for choosing USRobotics.
After reading your email we understand that you would like to confirm if the USR5637 supports Linux (Ubuntu). In this case we kindly inform you that, you need a USB modem driver (CDC ACM) compiled into a Linux kernel 2.4.20 or higher or as a loadable module for your kernel. Installation of the modem under these kernels is fully automatic provided your kernel has the Plug and Play module enabled (default). You do not need to install any drivers off the USRobotics installation CD-ROM.[/B]

Roland Burgan
[email]rburgan@up.net[/email]

---

### Post by 3rdalbum on 2008-03-20
Correct. The wording is a bit technical  (manufacturers assume that all Linux users are a cross between Linus Torvalds and Andrew Morton), and I'm not sure if they're saying that the modem will work out-of-the-box or that you will need to compile a module - but it's saying that it will be able to work.

---

