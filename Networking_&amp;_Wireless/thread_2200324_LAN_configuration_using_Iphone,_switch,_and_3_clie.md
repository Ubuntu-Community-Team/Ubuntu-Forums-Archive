---
title: "LAN configuration using Iphone, switch, and 3 clients"
date: 2014-01-18
forum: Networking &amp; Wireless
---

### Post by jdallara on 2014-01-18
Hello,

  I'm have set up a LAN for my office which is working well except for providing Internet access for all machines via an Iphone using its personal hotspot capability.  I have 3 PC's (desktop, laptop, desktop2) that are connected via a switch (diagram below).  They all communicate fine amongst themselves.  One PC (desktop) is also connected to the Iphone for internet access.  That connection works fine, PC to internet, PC to LAN.  The other PC's (laptop, desktop2) can see the Iphone via ping, however, I can't seem to figure out how to get them to route their internet requests through the first PC (desktop) to the Iphone.  I have packet forwarding turned on on the Iphone PC (desktop), but I don't know what else is needed.  Ubuntu 13.11

  laptop---------switch--------desktop-------Iphone
  desktop2-----//
  OfficeJet-----/

  client                   IP address              NetMask                 Default Route         Primary DNS
Iphone                   172.20.10.2            255.255.255.240      172.20.10.1            172.20.10.1
desktop                  172.20.10.10          255.255.255.240      
laptop                    172.20.10.11          255.255.255.240
desktop2                172.20.10.12          255.255.255.240
OfficeJet                 172.20.10.14          255.255.255.240

The Iphone uses DHCP for its address, the other clients are static.  I'll be glad to supply any other information that may be needed.

Thanks in advance,

Jon.

---

### Post by Zhivargo on 2014-01-20
This might be no help at all but you could tether them all through wifi :) 



but try pointing your DNS server on everything but the iphone to the iphone Default Route: 
```

client        IP address     NetMask               Default Route     Primary DNS
Iphone      172.20.10.2    255.255.255.240    172.20.10.1        172.20.10.1
desktop    172.20.10.10  255.255.255.240                                   ''
laptop       172.20.10.11  255.255.255.240                                   ''
desktop2   172.20.10.12  255.255.255.240                                   ''
OfficeJet   172.20.10.14  255.255.255.240                                   ''

```

you are doing something really strange IMHO. Are you sure you have to use an iphone like this?

 

what you are doing is really strange... post more info plz

---

### Post by jdallara on 2014-01-23
Sorry for the slow reply, was off-line for a couple of days.  Couple of reasons for not using WiFi.  My laptop's WiFi isn't supported and my phone is one of several phones on a business plan and we can't get WiFi hot spot capability.  I was originally hoping to use my desktop as a WiFi hotspot and having the Iphone tethered to it but that didn't work due to the laptop.  I've tried configuring the other machines to point at the Iphone as the DNS server but that doesn't work.  I'm thinking that the solution may involve setting up the desktop as a router that will handle the DNS and routing services but I'm not sure how to go about it.  I am able to move the Iphone to the laptop so I can access the web, but desktop2 is a new box and I upgraded the Iphone to IOS7 before I got it, so I can't get desktop2 and the Iphone to work together.  The Iphone refuses to permit the connection even though I tell it to trust the box.  The other 2 computers were connected under IOS6 so they were 'grandfathered' in and can still connect.  Desktop and desktop2 are running Ubuntu 13.11 and the laptop is 13.04.

Thanks,

Jon.

---

