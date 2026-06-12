---
title: "Network one computer from another?"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by explosive on 2007-07-30
Sorry for the topic title - I couldn't think how to best describe this question...

Basically I have one PC running Ubuntu 7.04 (server edition) and another running 7.04 (desktop edition). I have  managed to get the wireless network card to work on the server edition box but I cannot (after lots of posting on here and much troubleshooting) get the network card to work in the desktop edition PC.

I was thinking, is it possible to connect a network cable from the desktop to the server and get the server PCs network connectivity "shared" with the desktops box?
Would I need a crossover cable or would straight cable work?
How would I go about configuring this?

---

### Post by Synflux on 2007-07-30
You would need a crossover cable unless you plugged them both in to a switch in which case two straight-through's would be fine.

You'd need to configure static IP's on both boxes as it sounds like there is no router to hand out DHCP addresses?

---

### Post by explosive on 2007-07-30
Sorry - I'll be more specific!

I have a wireless router that is set to static IPs. I have 3 machines already hung off it wirelessly. The "server" box is working fine wirelessly, I would like to make the "desktop" box connect to the network via the "server" box.

---

### Post by xpod on 2007-07-30
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

Thats how i do it although i`m not using a wireless router in the first place so cant really tell you how this fits into the equation.
I`m buying a wireless router soon though i think as there is only so much wiring a man can hide:)

---

### Post by explosive on 2007-07-30
I want a combination of those setups though.

```

Router ----- PC
          ----- PC
          ----- PC
           ----- PC ----- PC

```
is that possible?

---

