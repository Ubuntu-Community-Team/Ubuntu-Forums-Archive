---
title: "Connected to new wireless router, but now Firefox can't find server"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by Monona on 2007-10-17
I am running Feisty Fawn on a Acer TravelMate 4010.

Ethernet Controller: Broadcom Corporation BCM4401 100Base-T (rev 02)
Network Controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

We set up a new wireless router at my apartment and now I can't get to the internet.  My wireless connection shows I'm connected at 58% right now, but Firefox can't find the server.  We're using WPA2 encryption, and it recognizes the password I enter.  It comes up with a message saying I'm connected.

I'm also unable to install new programs/updates.  In the Synaptic Package Manager I get the message "could not resolve 'us.archive.ubuntu.com'".

This is extremely frustrating because I was able to access other wireless networks until this afternoon when I tried to hook up directly to the modem.  I changed some of the network settings, but now both wireless and wired connections are roaming mode enabled.

Looks like other folks are having some of the same problems, but I'm new at this and don't understand the technical stuff.  

I'm super-annoyed that I spent 3 hours waiting around for the internet guy to show up this morning, then spent another hour hooking up the router, and now all my roommates have internet except for me. (i know that isn't relevant to fixing my problem.  just gotta vent)  Good thing they got internet, though, cuz I couldnt post otherwise.

Thanks.

---

### Post by scrooge_74 on 2007-10-17
You lost your DNS settings

Reboot the router so it picks them up from your ISP or add them manually to your PC so you don't have to depend on someone's else DNS config

[https://www.opendns.com/start](https://www.opendns.com/start)

DNS servers IP 208.67.222.222 and 208.67.220.220

---

### Post by Monona on 2007-10-17
WHOO-HOO!

SImple, effective way to fix it.  Thank you so much.  I was really worried that I was headed down a convoluted road of /etc/blahblah.conf files and pinging some sort of server somewhere.

scrooge_74, if you were my next door neighbor, I would totally hug you and bake you cookies.

Thanks again.

---

### Post by scrooge_74 on 2007-10-17
Glad to be of service, have fun on my account

---

