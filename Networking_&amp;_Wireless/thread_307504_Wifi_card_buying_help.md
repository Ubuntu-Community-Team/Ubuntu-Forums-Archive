---
title: "Wifi card buying help"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by peanut butter on 2006-11-26
hi, i have an acer wifi card in my laptop, its actually a linksys, it worked with ndiswrapper in dapper, but not in edgy.
so
1. anyone know how to gat a linksys internal card working?

and/or

2. What is a really cheep pcmcia wifi card that works out-of-the-box on 6.10?

---

### Post by FrodoB on 2006-11-26
Have you tried the latest version of ndiswrapper? 

Version 1.29

[http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

I guess I should also add that while Edgy is nice and I have no issues with it, Dapper is just as good, so why not stick with it?

What type of wireless device do you have?

---

### Post by peanut butter on 2006-11-26
i guess its a bit late for that. I sorta tried to update so it was crashed and is now formatted over.

EDIT: i dont want to use ndiswrapper 1.9 because i would have to recompile the kernel., and my wifi card is an ACER IP2220 which is actually a Linksys IPN inprocomm 2220 .

---

### Post by FrodoB on 2006-11-26
Well I am using ndiswrapper 1.29 on both Dapper and Edgy and I did not recompile the kernel and it works well with several devices. 

You might want to give it a chance.

---

### Post by peanut butter on 2006-11-26
ok , i took your advice, so now i get a dhcp offer, and it shows as me having an internal ip, but i cant connect to the router (smoothwall) or internet.](*,)

Update: Pigning dosnt work either.

---

### Post by wmatlock on 2006-11-26
Check out the following link and see if some of these articles don't point you in the right direction.

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

They really helped me solve my problems.

---

