---
title: "want to switch to ubuntu but !"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by chrischennai on 2008-02-20
Hello

Here is my present situation.

There are 15 computers networked. The other 14 computers connect to the internet via a gateway computer 

computer15.

Computer15 is running windows XP and it is running a proxy server also. So all 14 computers in LAN access computer15 to connect the internet.

Why ?

Because I have installed an excellent antivirus product in computer15 and I do not want to buy any more licenses of that antivirus So what computer15's antivirus does is, it processes all emails, webpages, files that are being downloaded to the other LAN computers..So since computer15 is the gateway and the proxy, it can scan all files that are downloaded "through" it and 

**ALL the other 14 computers are AUTOMATICALLY PROTECTED.**

But windows xp has its own share of problems and it is becoming slower and slower to access the internet since I read somewhere that an windows XP computer can serve a maximum of 10 network connections at a time.

=====================================


I want to use UBUNTU for the gateway  computer alone. All the other 14 computers will still use  windows XP

Can anyone please tell me

1) How or what do I do to make UBUNTU a true and SAFE proxy server. WHich is the best proxy software which gives me total access control etc ?

2) Here comes  the main reason which is preventing me from switching to ubuntu for the gateway. I assume *clamav* can be installed in ubuntu but what do I do or how to configure it such a way that each and every file or email or website that goes through the above proxy server gets scanned automatically ? This is important since none of the other 14 computers running windows xp will have any kind of antivirus installed . THEY all will depend on this ubuntu gateway computer for their dear LIFE !!

---

### Post by njparton on 2008-02-20
I suggest you look at specific firewall distributions such as m0n0wall which are designed to act as firewalls and/or gateways.

You could configure ubuntu to do this (and you will probably learn more in the process), but check out the specific distros first.

---

### Post by Junglizer on 2008-02-20
Don't forget Smoothwall and this would be a good application for OpenBSD as well.

---

