---
title: "Binding Samba to a network interface"
date: 2005-06-18
forum: Networking &amp; Wireless
---

### Post by mglukhovsky on 2005-06-18
I've been playing with Samba for the past few days (Linux<->Linux only atm.) I have a wireless network in the house for Internet access, but I put together a Gigabit network for file transfer among the PC's using Samba in my room so I could take advantage of the massive speed increase Gigabit offers.

I was having drastically slower access times and speeds than expected, when I realized that the computers were accessing each other over the wireless network! Is there any way I can block access to the Samba shares from my wireless cards for security and speed?

---

### Post by alastair on 2005-06-18
Yes - you can bind to specific interfaces. Look at the man page for smb.conf (or if you have samba-doc installed, /usr/share/doc/...).

---

### Post by mglukhovsky on 2005-06-18
Is it best to use the "hosts allow" parameter?

---

### Post by Gallows on 2005-06-20
Have a look at Chaper 4 of O'Rileys Using Samba

[http://www.rxn.com/services/faq/smb/using_samba/html/ch04_06.htm](http://www.rxn.com/services/faq/smb/using_samba/html/ch04_06.htm)

---

