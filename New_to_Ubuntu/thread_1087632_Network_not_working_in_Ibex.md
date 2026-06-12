---
title: "Network not working in Ibex"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by LiviooT on 2009-03-05
I just installed Ibex so I can try it out... and my network isn't working. This is my motherboard:

[http://www.asrock.com/mb/overview.asp?Model=ALiveNF6G-VSTA](http://www.asrock.com/mb/overview.asp?Model=ALiveNF6G-VSTA)

It starts searching so it can acquire settings (*Requesting a network address from the wired network*)and then a notification tells me "The network has been disconnected"...

Please help, I am a complete beginner... :oops:

Thank you, much appreciated :)

---

### Post by Iowan on 2009-03-05
In a terminal, enter:```
lshw -C network
```- post results.

---

### Post by brdmb on 2009-03-05
(to get to a terminal, click Applications->Accessories->Terminal)

---

### Post by LiviooT on 2009-03-06
resolved! just post installation bugs :D... I restarted my system and waited... and it found the network :) Enjoying my freshly installed Ibex right now :) thank you!

---

### Post by LiviooT on 2009-03-07
UPDATE:

It stopped working again...
I ran ```
lshw -C network
```

Result:

```
*-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e6:f4:2a:6a:ce:b7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

I tried fiddling with it but... to no avail...

---

