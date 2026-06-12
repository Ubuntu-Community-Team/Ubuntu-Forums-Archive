---
title: "Airport Express with Ubuntu 10.10"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by dunbrokin on 2010-12-12
I have tried setting up Airport Express using WIne and using VBox....neither can detect the Airport express. I can see the Airport Express in Network Manager.

Any suggestions?

---

### Post by golovan on 2010-12-27
Try "connect to other" in Admin Utility (wine). Type in the IP for the AEX (probably 10.0.0.1 or something) and password "public". Then you can set it up (it works for me).

To stream music check out Stream2IP.

---

### Post by dunbrokin on 2010-12-27
Thank you for that...it works....I can join a network....but am having problems extending a network....that does not seem to work for some reason.

---

### Post by Takkat on 2010-12-28
> **dunbrokin said:**
> I have tried setting up Airport Express using WIne and using VBox....neither can detect the Airport express.

To run the setup programm for an AirportExpress from VBox you need to install Apple Bonjour services. Runs fine with me. In Ubuntu Bonjour/Avahi has a limited capability to refresh services. Streaming is much more stable using the IP of an AEX directly (e.g. by using [ stream2ip]("https://launchpad.net/stream2ip")).

---

