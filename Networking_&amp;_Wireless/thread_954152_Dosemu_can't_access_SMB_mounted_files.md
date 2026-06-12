---
title: "Dosemu can't access SMB mounted files"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by anezch on 2008-10-20
Hi, I've been using ubuntu+dosemu+samba for about 2 years to run our old software developed in MS FoxPro 2.6 for DOS. They were run perfectly until I upgraded several PC to Hardy.

The problem is, I can mount remote databases with CIFS/SMBFS, read/write them from linux, but when I access them under dosemu I can list them, which means the files are detected, but can't read/write them.

Then I was thinking it's Dosemu's bug so I downgraded it from version 1.4 to 1.2. But the problem still persists.

Any Ideas?

---

### Post by emendelson on 2008-10-21
Usually I don't post links to things I haven't tested, but no one else seems to have pointed this out, so here you are:

[http://pascalek.pers.pl/en/propage/samba4dosemu-introduction](http://pascalek.pers.pl/en/propage/samba4dosemu-introduction)

I have NOT tried this, but it seems to be designed to do exactly what you are looking for. If you test it, could you please come back and report your results?

---

### Post by amit.sarda on 2009-02-05
i am facing the same problem.

i am a newbi and wanted how to load it.

i even wrote the following email to them and here is their reply.


[I]Unfortunately Ubuntu is a distribution witch base on Debian, therefor it is
using DEB packages and I'm not familiar with them. Sorry - I can't help. You
must find some DEB guru which could help you.

Regards,
--
Rafa&#322; Cygnarowski
[email]rafi@pers.pl[/email][/I]

did some1 know how to installed the same??

---

