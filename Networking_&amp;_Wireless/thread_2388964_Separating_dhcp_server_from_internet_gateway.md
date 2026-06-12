---
title: "Separating dhcp server from internet gateway"
date: 2018-04-09
forum: Networking &amp; Wireless
---

### Post by e_james on 2018-04-09
I've just had my broadband upgraded and now I need to use a vdsl modem. The new "super" router provided with the upgrade is unsatisfactory as a dhcp server. It only allows a maximum of 8 reserved IP addresses and I want more. If I'm counting correctly I have 11 devices connected to my home network via ethernet and another 8 via wi-fi. In most cases I need a known IP address for network shares and remote desktop operation. Almost all of them need to connect to the internet.

I have a Zyxel 16 port gigabit switch connected to a TP-Link router which connects to a Dynamode router which now connects to my new Huawei HG633 (Talktalk) vdsl router. The TP-Link router acts only as a switch - the ethernet connection between the Zyxel and the Dynamode won't work properly without it. I have turned off the wireless and dhcp functions in the Talktalk router. The Dynamode wireless and dhcp functions work well. The Huawei broadband connection is about as good as I can expect it to be, but I can't get any of my devices to connect to the internet. I'm writing this message on my laptop which is tethered to my phone. I can probably get the system to work by assigning fixed addresses to most of my devices, but I would prefer to avoid that much work.

Any suggestions and / or explanations would be much appreciated.

---------------------

Problem solved thanks to advice on another forum. I needed to fill in gateway and dns addresses on the Dynamode router. Essentially the Dynamode is just another computer with a fixed address. I wish I had thought of that much earlier.

---

