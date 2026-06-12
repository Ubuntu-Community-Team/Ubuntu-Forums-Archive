---
title: "Modem not detected"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by lionwag on 2008-06-20
I have just intstalled Kubuntu 8.04 in my computer.
KPPP is able to connect with my ISP correctly
through a standard external 56K modem.

Konqueror cannot go anywhere because the SYSTEM
(network settings) does not detect the modem.
It detects, and has enabled, the ethernet card OK.
How can I get it to detect the modem?

---

### Post by Sealbhach on 2008-06-20
How about trying

```
sudo wvdialconf
```

then also post here the output of

```
ifconfig
```



.

---

### Post by lionwag on 2008-06-21
Problem solved.  I simply disconnected the ethernet card
and the system defaulted to the modem, even though the modem
is not indicated in Network Settings.  :)

---

