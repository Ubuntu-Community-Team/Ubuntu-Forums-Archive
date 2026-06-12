---
title: "How to change DNS numbers? (Ubuntu 14.04)"
date: 2014-09-21
forum: Networking &amp; Wireless
---

### Post by zin3 on 2014-09-21
Hello! I'm using ubuntu 14.04, I'm trying to change my dns number without success. 
First I tried to change through the network manager but it doesn't let me save it, here a screenshot:
[ATTACH=CONFIG]256586[/ATTACH]

Later I tried to modify the resolv.conf file in /etc/resolv.conf but it gives me a alert:
[ATTACH=CONFIG]256585[/ATTACH] 
How can I change it? :confused:

---

### Post by jeremy31 on 2014-09-21
> **zin3 said:**
> Hello! I'm using ubuntu 14.04, I'm trying to change my dns number without success. 
First I tried to change through the network manager but it doesn't let me save it, here a screenshot:
[ATTACH=CONFIG]256586[/ATTACH]

Later I tried to modify the resolv.conf file in /etc/resolv.conf but it gives me a alert:
[ATTACH=CONFIG]256585[/ATTACH] 
How can I change it? :confused:

For the first pic, leave it in method-auto(DHCP) and add the DNS numbers you want and should be able to save

---

### Post by zin3 on 2014-09-21
> **jeremy31 said:**
> For the first pic, leave it in method-auto(DHCP) and add the DNS numbers you want and should be able to save

[FONT=arial]Thanks, I did it and I was able to save it, but apparently It didn't replace the dns number, I tried to check through the opendns test page and it says that I'm not using it[/FONT]
[ATTACH=CONFIG]256587[/ATTACH]


[FONT=arial][COLOR=#000000]It looks like instead of replace the old dns[/COLOR][COLOR=#000000] number it just added the new one without remove the others, check this out:[/COLOR][/FONT]
[ATTACH=CONFIG]256588[/ATTACH]

:(

---

### Post by Bucky Ball on 2014-09-21
Edit the wired connection again and get rid of the unwanted DNS numbers ...

---

### Post by zin3 on 2014-09-21
Hey, I solved the problem, on the network manager I just switched to method to "automatic (DHCP) addresses only"

[ATTACH=CONFIG]256592[/ATTACH]

Thanks for helping, topic solved :eek:

---

### Post by fadli3 on 2014-11-15
But how you can change that? I already save new dns and I do all of you do, but my dns never going change? help pls :(

---

