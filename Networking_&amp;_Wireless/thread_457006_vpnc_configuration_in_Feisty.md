---
title: "vpnc configuration in Feisty"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by Bosonator on 2007-05-28
Hello,

Previously under Edgy Eft, I was able to get wireless working beautifully on the Broadcom wireless network adapter in my Compaq Presario laptop. As well, I was able to connect to my university's Cisco VPN wireless network using vpnc. 

Now, using Feisty Fawn, I run into some problems. When I try to run it, I get an error saying "unknown host vpn.dal.ca". I dual-boot with Windows, where I (successfully) use the university's 'official' vpn client, and "vpn.dal.ca" does appear to be the correct hostname. 

My first question: is there something obvious that I might be doing wrong?

My second question: Could this have anything to do with the ndiswrapper driver problems in Feisty? I'm able to connect to the internet (thanks to Compwiz's [script]("http://ubuntuforums.org/showthread.php?t=197102")), but not to WPA-enabled access points, so I was wondering if there's a similar bug that prevents the use of vpnc.

If I can't get this to work, I guess I'll have to roll back to Edgy (which would be too bad... Feisty is pretty slick otherwise).

Thanks a ton!

---

### Post by VorDesigns on 2007-06-02
I can't connect either and I'm wondering if anyone has some suggestions or places to look for logs or anything.  The KVPNC in gnome I added doesn't seem to function and when i run it via a terminal, it prompts for everything and never comes back.

---

