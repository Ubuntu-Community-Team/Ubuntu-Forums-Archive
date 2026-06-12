---
title: "Internet via Bridged Connection from Windows 7 host"
date: 2014-03-22
forum: Networking &amp; Wireless
---

### Post by theo.langsnoer on 2014-03-22
I installed Ubuntu 12.04.3 LTS on my new Toshiba Satellite. Unfortunately the WIFI is not working. I tried to connect my lan port with a crossover cable  to a Win7 laptop with a bridged connection. How do I setup the Ubuntu side of this connection? My Toshiba has a Realtek RTL8188ee network card. Once I have this connection working, I can update my Ubuntu installation and download the right driver for the network card.

---

### Post by houstonbofh on 2014-03-23
As far as Ubuntu is concerned, just plug it in.  It is already configured with DHCP.  However, your network may be a different story.

---

### Post by theo.langsnoer on 2014-03-23
My network is not more than a crossover cable between the two laptops. On the windows host, I see that the bridge connector takes over the wifi connection, which I understand is correct. At the Ubuntu side, I get response if I ping the host. Unfortunately, the internet is unreachable which I tested with pinging 8.8.8.8

---

### Post by houstonbofh on 2014-03-23
If you can ping the Windows box, and the gateway is correct, Linux is not the problem...

---

### Post by theo.langsnoer on 2014-03-24
> **houstonbofh said:**
> If you can ping the Windows box, and the gateway is correct, Linux is not the problem...

What should the default gateway be?

---

### Post by houstonbofh on 2014-03-26
Whatever your router is.  What is the default gateway on the Windows box?

---

### Post by theo.langsnoer on 2014-03-28
I'm sorry for the delay. Been away for a few days.
Default gateway on the windows box is 192.168.180.1

---

