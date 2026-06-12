---
title: "Slow or no network response when using Feisty"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by stil on 2007-08-12
Hello there.

I'm having some issues with internet response times when using FF to browse. I'm sitting next to a friends Windows box with his router plugged into my laptop. His connection works fine through the Win box, but when I use it I'm constantly having to reload unresponsive websites. Other times they don't work at all. Again, if I unplug and go back to his Winbox, things are fine and I can browse normally. With Feisty... the page I'm writing in right now has been loading since I started typing. A bit silly, really. I don't know where to start looking for a cause.

Network stats in sysmon show the usual peak - long flat - peak information of what I assume is a ping request.

At the time of writing this FF is still "Transferring data from ubuntuforums.org"  and the network history is practically dead :confused: This is symptomatic of about 90% of the sites I visit. They load for a few seconds then stop while 'transferring data'.

---

### Post by tenbbs on 2007-11-24
Having a similar problem with Xubuntu 7.10. Fresh install, all of the networking works, but from the time I hit enter with a new web-address, until the time that site shows up, we're talking about 5 seconds or more.

Also I've noticed that when I pull down new packages, it waits and waits for 5 seconds or so, and then pulls down all 8 or 9 of the package related files relatively quickly. So it's not a pure speed issue, I'm defintely having some kind of delay between the time I hit enter and the time the requested data comes back to the computer.

Running an HP laptop AMD64-3700+, ndiswrapper driver for my Broadcomm wireless, BUT the same speed/delay problem takes place when I'm hardwired in with CAT5. And of course, when I boot into Win, this speed/delay problem doesn't exist.

-HelicopterJay

> **stil said:**
> Hello there.

I'm having some issues with internet response times when using FF to browse. I'm sitting next to a friends Windows box with his router plugged into my laptop. His connection works fine through the Win box, but when I use it I'm constantly having to reload unresponsive websites. Other times they don't work at all. Again, if I unplug and go back to his Winbox, things are fine and I can browse normally. With Feisty... the page I'm writing in right now has been loading since I started typing. A bit silly, really. I don't know where to start looking for a cause.

Network stats in sysmon show the usual peak - long flat - peak information of what I assume is a ping request.

At the time of writing this FF is still "Transferring data from ubuntuforums.org"  and the network history is practically dead :confused: This is symptomatic of about 90% of the sites I visit. They load for a few seconds then stop while 'transferring data'.

---

### Post by crjm on 2007-11-24
I had a similar problem, then found this link: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

After I disabled IPv6, my connection became significantly faster.

---

### Post by tenbbs on 2007-11-25
This seems to have worked. I also went into Firefox and did about:config and turned on net.dns.disableipv6 and that had an immediate result.

I'll have to wait till I'm installing another package or downloading a file to test it for certain, but for now DNS request responses have returned to a completely normal and acceptable speed. Thx for the help.

-HelicopterJay

---

