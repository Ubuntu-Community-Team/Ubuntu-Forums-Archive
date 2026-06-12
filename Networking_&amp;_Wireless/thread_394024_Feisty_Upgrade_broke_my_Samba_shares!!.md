---
title: "Feisty Upgrade broke my Samba shares!!"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by baldercm on 2007-03-26
Hi!

I've just upgraded to Feisty. Everything except my Samba shares are ok. We've two laptops at home, one with Ubuntu (and VMware/WinXP) and one with Ubuntu/WinXP dual boot. If I try to access to samba shares using Ubuntu, everything goes fine, but in WinXP(both from the dual boot or from my VMWare WinXP) I can't even see my share folders or access my workgroup machines, I get an error window saying:
```
I can't access MYNETWORK. You probably don't have sufficient permissions.... Contact system admin...
The server has not been set up for transactions
```
(sorry for my translation mistakes....)

I've just tried and I can access my shares if I write the name on the Windows Explorer address bar (\\johndoe\foo).

I need this working soon since I use it to work and I need my WinXp network drive! 
I'm sure all this start happened since I upgraded to Feisty. Anybody knows why and how to fix it?

---

### Post by Fenix-TX on 2007-04-20
The same here.

Solved deleting the shared folders and adding them again

---

