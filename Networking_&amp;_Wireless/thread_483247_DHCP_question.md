---
title: "DHCP question"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by WizardInSmoke on 2007-06-24
Can anyone eplain to me how i would go about setting up  dhcp my ubuntu server 7.04 so that i can have the internet connection coming off the modem into the server box, then from there to a switch to my other computers?

i have 2 10/100 nic cards in already i just need some help with setting up the dhcp, i do not know anything about how to so anyone that can help me from scratch, on a fresh install of serverv7.04 it would be really appreciated

Thanks

WizardInSmoke

---

### Post by scrooge_74 on 2007-06-24
You need to install the DHCP server package and point it to use one of your cards.  To tell you the truth I never quite manage to get that working very well because I had to receive DHCP from the ISP for the server and then if I try to give IPs to the other PCs the DHCP server would not work, it would work only if I was not receiving DHCP from my ISP.

I had to settle with static IPs for my lan, but I am sure there is a way out there or in the DHCP3-server documentation

---

### Post by Mr. C. on 2007-06-24
It sounds like you want your Ubuntu box to act as a router ( to route traffic to / from the internet for your other computers ).

If so, don't worry about DHCP right now - this isn't a DCHP issue.  DCHP just assigns addresses, which you can do manually.  Once you have routing working, you can setup the DHCP server to assign IPs.

Do you have your network cards up and running (eg. internet-connected card functions allowing server to connect to internet, LAN-facing card and LAN systems can ping each other)?

MrC

---

