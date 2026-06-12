---
title: "How do I connect to a Wireless Network from Terminal-only?"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by drkameleon on 2009-06-12
Let's say I wanna boot Ubuntu in just-terminal mode (without GUI).

How could I do the following stuff?

1) View the list of available networks
2) Pick one to connect to

Thanks in advance! ;)

Dr.Kameleon

---

### Post by hayden92 on 2009-06-12
View available wireless networks:
```
iwlist <interface> scan
``` (Replacing <interface> with your wireless interface [for example mine is eth1)

If you don't get any networks listed:
```
ifconfig <interface> up
```
To turn on your wireless interface.

If your wireless network is WPA encrypted:
```
iwconfig <interface> essid <network name> key s:<network password>
``` 
(Note: I use "s:" so that I can enter my key in ASCII form e.g. "Kll4Wx"

If your network isn't secured:
```
iwconfig <interface> essid <network name>
```

I hope this helps, if you want more help just let me know!

Hayden

---

### Post by drkameleon on 2009-06-12
Hmm... Sounds simple. I'll try that out.

Thanks a lot, Hayden! ;)

---

### Post by kevdog on 2009-06-12
Ive written a huge tutorial on this matter with the link in my signature.  

Good Luck!

---

### Post by drkameleon on 2009-06-12
> **kevdog said:**
> Ive written a huge tutorial on this matter with the link in my signature.  

Good Luck!

Thanks Kevdog! I'll have a look at your tutorial.

---

### Post by nandemonai on 2009-06-12
> **kevdog said:**
> Ive written a huge tutorial on this matter with the link in my signature.  

Good Luck!

Awesome tutorials kevdog. ;)

---

