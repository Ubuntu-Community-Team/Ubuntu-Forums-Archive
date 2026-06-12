---
title: "Extremely slow downstream but upstream fine on 3com 3C905c"
date: 2005-04-21
forum: Networking &amp; Wireless
---

### Post by dejitarob on 2005-04-21
This is a very strange problem and I am a bit at a loss on what I can try. My Dell GX400 at work gets around 5KB/s downstream and the normal 300KB/s upstream on a 100Mb connection, according to dslreports.net speedtests. In WinXP, the connection is fine. This is only in Ubuntu Hoary 5.04, both in the 2.6.10-5-386 and -686 kernel. I'm forced to use Windows since browsing sites and checking email is extremely slow (gmail won't even load). Anyone have any ideas?

---

### Post by steward75 on 2005-07-23
I too have a Optiplex GX-150 and have the same 3com 3x905c nic card and encountering the same exact thing.  Do we know why this happens?  Does someone out there know how to change the settings loaded for the nic card as far as full/half duplex, 10, 100, or 10/100, autodetect settings?

Help is appreciated.

---

### Post by michellembrodeur on 2005-07-26
[QUOTE=dejitarob]This is a very strange problem and I am a bit at a loss on what I can try. My Dell GX400 at work gets around 5KB/s downstream and the normal 300KB/s upstream on a 100Mb connection, according to dslreports.net speedtests. In WinXP, the connection is fine. This is only in Ubuntu Hoary 5.04, both in the 2.6.10-5-386 and -686 kernel. I'm forced to use Windows since browsing sites and checking email is extremely slow (gmail won't even load). Anyone have any ideas?[/QUOTE]


Same here. Do this. change from automatically configure DNS to manually telling it what it is.

I use a router and manally put in DNS and alternate DNS address for my ISP and zoom fast up/down.

Just change it in yoru network configurations. to manually DNS.

---

### Post by Imgonna on 2005-07-26
Sorry to hijack a thread..

I have exactly the opposite problem.  Downstream on ADSL near line speed of 1Mb/s, upstream should be 256Kb/s, but from my new shiny Ubuntu lappy  (using wireless card, Belkin with Realtek chip set) it only pushes out around 56Kb/s.

The result is fast web browsing but a real pain when ftp upload and/or sending big emails.

Ideas?

I guess some network card settings?

Cheers

Glen

---

