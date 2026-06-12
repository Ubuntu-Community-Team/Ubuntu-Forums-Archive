---
title: "Complied kernel, now no internet on Linksys WUSB11 v2.8"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by ManOnOneWheel on 2007-08-23
In my house, we still have dial-up (arg) so I find it mush easier to connect to the internet on windows with the family computer and then use the wireless router to connect to the internet in Ubuntu, thus I have no wired internet connection available, only wireless.

Alright, in an attempt to get hardware monitoring working on my desktop, I downloaded and compiled the latest stable kernel, 2.6.22. Under generic Feisty, my Linksys WUSB11 ver.2.8 network adapter was recognized, and worked great connecting the the wireless network, but under 2.6.22 I got nothing. It doesn't even seem to realize it's plugged in although the lights light up on the adapter. lsusb returns only zeros.

I've tried using ndiswrapper to load drivers, but ndiswrapper -l returns invalid driver. I have tried the drivers off the CD that came with the adapter, the drivers off the linksys website, and some recommended drivers off of ndiswrapper's site.

From what I understand so far, I may have not compiled the kernel correctly to recognize the adapter, or the new kernel does not natively support the adapter, either way, I would like to get my internet back so I can download the packages I need to see if my new kernel recognizes my hardware snesors.

Phew! what a post, I hope someone can help me, i'd hate to give up on the new kernel.

---

### Post by ManOnOneWheel on 2007-08-23
Anyone?

---

