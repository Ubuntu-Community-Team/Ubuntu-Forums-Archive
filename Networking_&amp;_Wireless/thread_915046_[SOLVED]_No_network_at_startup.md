---
title: "[SOLVED] No network at startup"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by Zboonet on 2008-09-09
Hey Guys !! :-)

I just moved to Ubuntu 8.04 LTS .. I'm happy, but there just one small issue.

Let me explain :
I have an old PC (Athlon 1300, no comment). And when I start, I have to manually click at the top-right of the screen the small computer with a red exclamation point and check a radio buton "Wired Network" .. otherwise, no network at all .. bad luck .. I'm still wondering how I'm still alive ;-)

Anyway, I don't find many subjects on this (or maybe I don't know how to search) ..

Does someone have an idea ?

Thanks a lot!
Zboonet

---

### Post by Nopposan on 2008-09-09
So, you can connect if you click the radio button, right?

I think you need to go to System --> Administration --> Network, and configure your network connection.  However, it could be more complicated.

---

### Post by Iowan on 2008-09-09
I'm still kinda old-school, so forgive me.  Check **/etc/network/interfaces ** file for an "auto eth0" line.

---

### Post by Zboonet on 2008-09-14
Hi :-)

Thanks for your answers.

System --> Administration --> Network Doesn't give me anything .. I see a window opening .. but, I don't see any option which permits the interface to be launched at startup ..

I looked to me /etc/network/interfaces file. Here is the content :

```
auto lo
iface lo inet loopback eth0

```

Should I replace the "auto lo" by "auto eth0". I think i already tried a couple of weeks ago ..

Thanks a Lot ! :-)
Cheers !!

---

### Post by Iowan on 2008-09-14
> **Zboonet said:**
> 
Should I replace the "auto lo" by "auto eth0". I think i already tried a couple of weeks ago ..NO... the system needs the loopback device.  Rather than replace, add the line(s):```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

---

### Post by Zboonet on 2008-09-15
What a wizard you are !!!!!

It works ;-)

Wonderfull !! :-)

Thanks a lot !! :-)

Cheers,
Zboo

---

