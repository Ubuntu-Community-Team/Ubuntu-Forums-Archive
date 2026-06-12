---
title: "Netgear WN1000RP extender"
date: 2014-10-23
forum: Networking &amp; Wireless
---

### Post by Mr Nemo on 2014-10-23
Hello!

I can't seem to get my computer to connect to my netgearWN1000RP extender. The extender shows up in my list of wireless networks, but when I try to connect the attempt lasts indefinitely. The few forums that I've found on google have given me little to no help. Any help is appreciated. Thanks.

---

### Post by CaptainMark on 2014-10-24
Well I can give some advice but not much help.Your post doesn't really belong here because it's not Ubuntu at fault, I bought the exact same range extender a few months ago and found the same problem, with all my laptops, my android phones, my chromecast. If and when it did decide to connect, I would get booted off after minutes. Range extenders are basically a waste of money unfortunately, they rarely give the results people are expecting. I sent mine back for a refund and instead for the same price bought a new router with a much more powerful antenna than my current router and that out performed the range extender by a long shot, now I can get wifi signal all over my house no problem. If your using the router that came from your isp as most people tend to, it won't be hard to get a better one pretty cheaply, you'd have a hard time finding a worse one to be honest.

---

### Post by Vladlenin5000 on 2014-10-24
Extenders rarely give the results people are expecting because "people" rarely configures them appropriately. An extender shouldn't be visible in the network as a standalone AP. It should instead connect to the router's AP and _extend _its range but keeping the same SSID -> If you see both networks (APs) you already did something wrong...
Properly configured, users can't easily know where they're connecting to because devices are supposed to 'roam' between one or another depending on the signal intensity.

Please follow the instructions to configure your extender. It should be as easy as connecting Ethernet cable, accessing its webserver config page in a browser, selecting the required profile, searching for and authentication in your current network, done.

---

