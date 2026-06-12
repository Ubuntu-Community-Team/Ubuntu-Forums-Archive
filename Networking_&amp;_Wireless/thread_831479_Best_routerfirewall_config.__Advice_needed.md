---
title: "Best router/firewall config.  Advice needed"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by tuproxy on 2008-06-16
I am setting up a firewall/router and need help.  I want this to be as secure as possible.  I am considering setting up a DMZ and wanted to know if I should add a third NIC card for a dedicated DMZ. Is this needed or not?  Can it be be run off the the other NIC that serve's the rest of the network?

Also, can anyone tell me a good tutorial for understanding IPtables?  I have been using the linksys 54WRT54g for some years and fully understand the diferent permissions there, so I guess i kind of understand routing.  Should I be reading more that that?  

Are there any other tips that can make my router EXTRA secure?  I will be using OpenVPN on my network to connect to business partners networks to do work.  Thanks.

---

### Post by dmizer on 2008-06-17
several things here

i would not suggest trusting a consumer level router like the wrt54g for handling business traffic.

a well configured linux setup could handle what you're needing to accomplish, but it would require someone with more advanced network/routing/nat/iptables experience than you can glean by looking over a few howtos and forum posts.  you're talking about knowledge that comes from lots of classroom time, and years of real world practical application experience.

the reason i say this is because it's one thing for you to play with these configurations at home.  but when you start to consider connecting to business partners and work, you're looking at something that has a direct effect on your livelihood, as well as your business partner's work (and livelihood), and likely very sensitive data.  this is not something to take lightly.  And, something way way outside what i would consider exposing to a DMZ.

so unless i have misjudged your needs by what you've posted, my suggestion here is to purchace some heavy duty equipment, and defer to someone local to you with lots of knowledge. start by looking under the ubuntu loco teams forums here: [http://ubuntuforums.org/forumdisplay.php?f=183](http://ubuntuforums.org/forumdisplay.php?f=183) and make some inquires about experienced local members who are willing to share hands on time and experience to help you get up and running.

sincerely, i'm not trying to belittle you by suggesting that you cannot handle this on your own.  in all seriousness, if i was put in the same situation, i personally would defer to more experienced help.

---

