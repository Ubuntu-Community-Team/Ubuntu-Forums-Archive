---
title: "[SOLVED] Wired Connection is not showing"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by DualJazz on 2008-11-23
Hello, my internet is letting me down in Ubuntu. I have had random times when the internet does work but about 80% chance the internet doesnt work in Ubuntu. Internet works fine on my other Ubuntu machines but not this one.

So what the question is, is that Why dosnt the internet appear to be working? Why isnt Wired Connection showing in Network?

The only options given in the Network part is one with the Cable going into a socket, and one with a phone. I am using a ADSL router/modem :confused: that is connected by a main internet cable. How I am connected to it is by using a network cable. Broadband.

The internet works on Windows XP and is dual booted with Ubuntu.

Any help is appreciated :)

---

### Post by Michael.Godawski on 2008-11-23
Hi, 
some data would be nice. Can you post the result of the following commands?

```
sudo lshw -C network
lspci
ifconfig
```

If you know the exact type of your adsl modem perhaps you can browse your way through starting here:

[LIST]
[*][https://help.ubuntu.com/8.04/internet/C/adsl.html](https://help.ubuntu.com/8.04/internet/C/adsl.html)
[/LIST]

---

### Post by DualJazz on 2008-11-23
Solved it. Found advice from the internet. Works now, strange but horay it works :)

Thanks for your help :)

---

