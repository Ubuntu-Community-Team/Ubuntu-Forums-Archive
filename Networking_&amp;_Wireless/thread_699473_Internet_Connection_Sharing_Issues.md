---
title: "Internet Connection Sharing Issues"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by duiu on 2008-02-17
I have a (slightly) complicated network setup that I am trying to get to work with Ubuntu. I have a Wireless Router in the kitchen that gives my Windows PC in my bedroom Internet access. In my bedroom, I also have a Ubuntu box and an Xbox that all connect to my Windows PC via a D-Link Wired Ethernet Switch (DSS-5+). Before I had the Ubuntu box, I just had the Xbox and computer connected via a Linksys  Wired Router with internet connection sharing providing internet access to the Xbox. I plugged my Ubuntu computer into the router and set it up with DHCP to get 'Net, but nothing happened. I tried a static IP and manually entered the gateway (my Windows computer's IP), but the Ubuntu box still had no Internet. I then swapped the Linksys router for the D-link router that I mentioned earlier and set the Ubuntu box on DHCP, and I got Internet. Yay. Then I shut the Ubuntu box down, and came back the next day. All the settings are the same, but I'm not getting Internet. Firefox gets stuck at "looking up www.whateversite.com". I can't figure out why it worked yesterday, but not today. Perhaps a DNS issue? Any suggestions?

My Xbox does get Internet, so I know the ICS is working.

---

### Post by duiu on 2008-02-19
I solved my own problem. It was a DNS issue. I changed my ethernet connection to a static IP and manually entered the gateway. For DNS, I set the IP addresses to be those of [OpenDNS]("http://www.opendns.com"), however I do believe that if I ran in the Windows (ugh) command prompt and entered the command ```
ipconfig /all
``` I could have found my ISP's DNS and entered that in.

---

### Post by Iowan on 2008-02-19
Congrats!! Mark this one [SOLVED]...
(Under THREAD TOOLS)

---

