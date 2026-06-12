---
title: "Intel PRO/Wireless 3945 problems with WEP"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by mattforni on 2008-08-21
So I have a bit of a weird problem.  I just upgraded to Heron and am now having trouble connecting to my 128-bit hex secured wireless connection.  I have no problem connecting to unprotected wireless networks such as the one at work or at friends houses, only my home secure network.  Any help or suggestions would be appreciated.  Thanks.

- Matt

---

### Post by airjaw on 2008-09-14
> **mattforni said:**
> So I have a bit of a weird problem.  I just upgraded to Heron and am now having trouble connecting to my 128-bit hex secured wireless connection.  I have no problem connecting to unprotected wireless networks such as the one at work or at friends houses, only my home secure network.  Any help or suggestions would be appreciated.  Thanks.

- Matt

This is a known problem, that numerous users are experiencing (including me).  I'm just posting here to tell you that you aren't crazy and its a real bug.  And that there isn't any fix (that I've seen) yet.

---

### Post by arheon on 2008-10-18
I've got Ubuntu 8.10 beta and the problem still exists... I've read that the problem is related with kernel somehow O_o

Machine - Lenovo 3000 N200

---

### Post by cakmin on 2008-10-18
I used to have a similar problem and have solved it by doing two things:
1. Changed the encryption of my wifi router to WPA (WPA-PSK)
2. Installed linux-backports-modules-hardy-generic from the unsupported updates source. Do some searching here with keywords such as "wireless, intel PRO/wireless 3945" and my username as the poster. I cannot remember the website that has the instructions about how to install it. I hope this helps you all.

---

