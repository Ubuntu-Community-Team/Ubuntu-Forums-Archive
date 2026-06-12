---
title: "Router Problem"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by LostBear on 2007-04-08
Hi

I just got a d-link router and wireless access point. (its a DSL-G624T). Ive got my main machine wired into one of it 4 ports and i use the wireless part for my laptops. 

The problem is i cant get firefox to dislay any web pages, it times out everytime. (trying google and bbc.co.uk so i know the sites arnt dead)

I know ive configured the router properly becuase i can access the routers setup up pages through firefox in ubuntu, and ubuntu will quite happily download updates for the operating system so that suggests that ubuntu is getting a net connection through the router, but firefox isnt seeing it for some reason.

Im dualbootiing with windows XP which is where im typing this, which again means the router is setup just fine.

Any help? Oh, ive gone through the netork tab in firefox and changed the network settings to automatic detect and that didnt work.

Anyone no the soloution to this?

cheers.
LB.

---

### Post by sharke on 2007-04-08
Go to Routers web admin page (192.168.1.1 in my case) and to the DHCP button on the Home tab.
Change the DNS mode from auto to manual and enter your ISPs DNS addresses.
Regards
Sharke

---

### Post by LostBear on 2007-04-08
thanks shark. it didnt fix the problem though.

any other suggestions?

---

### Post by LostBear on 2007-04-08
it lives!!

i suddenly remembered trying to setup my speedtouch over a month ago. this worked fine on release 5 but i couldnt make it go on 6.10 and gave up. so i booted off the live CD and the internet worked straight away....so i reinstalled 6.10.

Happiness!

thanks for the help **sharke**.

---

### Post by sharke on 2007-04-08
Thats great to see you fixed the prob.
Regards
Sharke

---

