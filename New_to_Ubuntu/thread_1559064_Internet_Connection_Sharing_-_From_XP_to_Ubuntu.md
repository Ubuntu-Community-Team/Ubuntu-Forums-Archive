---
title: "Internet Connection Sharing - From XP to Ubuntu"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by Zeppelin! on 2010-08-23
Okay, so I have a tower computer (Xp box) which is connected to the internet, and I wish to share the internet connection from it to a laptop (Ubuntu box), via ethernet LAN.

So, I connected the two via ethernet ports, and selected my internet connection on the XP computer and told it to enable internet connection sharing. Boom. The Ubuntu box connected nearly immediately, and I spent the next good while getting an updated package list and installing VLC. Shortly after I finished with this (I have dial-up, so it took a good long while), the connection dropped on my ubuntu machine.

I tried reconnecting, no luck. I tried adjusting the cable, no luck. I doublechecked everything, no settings were different from the working setup. I shutdown both systems and disconnected them, started the tower and reestablished internet connection, started the laptop and reattached the ethernet cable (causing an automatic logon attempt), still nothing.

I've been looking for a while at internet connection sharing documentation and other posts on this forum, but I haven't been able to figure out the exact course of action I should take. I am fully ready to blame the tower for this.

Now, one interesting feature is, this is what Windows tells me with ipconfig:
Ethernet adapter Local Area Connection:
    Connection-specific DNS Suffix:
    Autoconfiguration IP Address: 169.254.105.31
    Subnet Mask:255.255.0.0
    Default Gateway: 

Yes, the ones that are blank are in fact blank. I'm at a loss as to how to correct this, though.

To remove an 'obvious' suggestion: No, I cannot reverse their roles.

Thanks for any assistance you may be able to render, dear reader.

---

### Post by LowSky on 2010-08-23
are you sure both ethernet ports are infact working? the green light should turn on both when the plug in, and a yellow light will blink when data is sent over the line.

Recently I hade a ethernet port go dead on my motherboard and before that I lost one on a laptop. Equiptment can fail, so check it out.

If they both light up, then try to ping each machine

the terminal command is the easiest.

just type ping followed by the other comuters IP adress

ex:

```
ping 192.168.0.1
```

---

