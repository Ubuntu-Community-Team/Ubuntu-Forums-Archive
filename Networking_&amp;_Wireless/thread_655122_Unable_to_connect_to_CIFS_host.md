---
title: "Unable to connect to CIFS host"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by fairfield on 2007-12-31
Hi everyone,

Can someone help with this problem, which is driving me crazy.

I work in a small office and we have two Ubuntu 7.10 laptops. The main office computer has Windows XP Pro and a couple of printers. I have internet connection on the laptops via an access point. Both laptops connect to the internet without problems and can see the other computers on the network, exchange files, etc. No problems here. The problem is that when I want to print on one of the Windows printers, one laptop (a Fujitsu P-series Lifebook) works fine and prints on all Windows printers. The other one (a Medion laptop) does not print and gives me the message: "Unable to connect to CIFS host". I am unable to find any difference between the settings of the two laptops. Where do I find the difference so that I can use it to correct this problem?    

fairfield

---

### Post by HermanAB on 2008-01-01
Hmm, check it with telnet:

$ telnet printeserveripaddress 9100

and see what response you get.

Cheers,

Herman

---

