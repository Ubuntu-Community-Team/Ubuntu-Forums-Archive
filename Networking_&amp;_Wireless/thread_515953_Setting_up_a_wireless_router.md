---
title: "Setting up a wireless router"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by Hex_Mandos on 2007-08-02
I'm planning to set up a wireless connection at home. I need to know a few details:

1) Are routers a problem like wireless cards are? (thankfully, my wireless card works with Ubuntu)

2) If so, what brand is more Linux friendly?

3) Any other tip for a wireless noob?

Thanks.

---

### Post by spd106 on 2007-08-02
It's good to hear that you have a working wifi card. There should not be any problems with wireless routers that are certified by the Wifi Alliance (look for the Wifi logo). They all work with standard Ethernet and 802.11b/g, and usually have a web based interface for configuration.

If you're just interested in a consumer level black box that just works, then I used to recommend Belkin because they were often cheaper and had good support, but I've encountered problems with some of the recent iterations of their wireless routers, though I could just have been a little unlucky. All brands are much the same these days, so shop around and compare on price, features and support options as you would do for any other piece of kit. 

If you're after something a bit better and/or want to do some tinkering, you could look for a router that supports open source firmware from the [OpenWRT]("http://OpenWRT") project. This means you can add new features and customise it to your liking. Not all wifi routers are capable of running this, so you have to be selective. The [WRT54GL]("http://en.wikipedia.org/wiki/WRT54G") (L for Linux) seems to be the most highly regarded (I have one!).

If you're looking to run a home server then it's probably a good idea to look out for dynamic dns (DDNS) support, most of the newer routers have it. UPnP has become popular too, though I turn it off.

---

### Post by lisati on 2007-08-02
The Netgear router which I use, and which I installed before I discovered Ubuntu, covers both wireless and wired. For the most part, the default settings were fine. Once I'd put Ubuntu on my desktop and laptop it didn't need any changes to its settings, and Ubuntu seems happy enough using it without any hassles.

EDIT: Don't be scared of checking out security options like WEP or WPA (which will require potential users to use a password) and "MAC" access control (which limits which computers can connect, even if they do have the right password). And don't forget to change your chosen router's administrative password.

---

### Post by Hex_Mandos on 2007-08-04
Thanks for your help. I bought the cheapest router around, but I'm using it just as an access point (I tried to replace my small network switch with it, but the connection was far too unstable for both wired and wireless clients). Now it seems to be working flawlessly. Now I just need to configure the security options.

---

