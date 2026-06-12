---
title: "Slow uploads from Feisty to Edgy-Samba server"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by galileux on 2007-08-17
Hi

I'm running Feisty amd64 and I've got quite poor throughtput to SMB, only about **1.4MB/sec **upload to Samba shares and about 5.5MB/sec download.

This client runs on Intel Core2 Duo E6600 hosted by an **Asus P5B motherboard**, with Realtek Gigalan on-board (which I had to disable in favour of an old Realtek 10/100).

There is another client, a Dell Inspiron laptop running XP, accessing the samba shares at much faster speeds.

I booted the Feisty-32 live CD into the Dell, tested the transfer with scp -r and got much better speeds (about 8.9 MB/sec upload).

Am I sitting on a piece of crappy hardware?
Is it already time to ditch the Asus P5B Mobo?
Or perhaps it is a problem related to the 64-bit versus 32-bit architecture?

It's got to be one of those two, since we've more or less ruled out anything else that we could think of... unless someone can suggest something else we can try.

Thanks for any help
Galileux

---

### Post by galileux on 2007-08-17
Forgot to mention: I also booted the CoreDuo into a Feisty-32 Live CD: same results: 1.5 MB/sec average from client to samba share.

---

### Post by AnRkey on 2008-02-14
I have super slow speeds here on multiple clients of various types, from winblows and/or ubuntu.

Is samba just slow or is there something I need to fix in my config?

Any help would be cool.

---

