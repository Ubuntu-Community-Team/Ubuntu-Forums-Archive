---
title: "lan is a ghost"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by technoplume on 2007-12-13
I just installed 7.10 and started using it. Then I notice that the network was not working. So I did some research in the system and can't find the solution. Both eternet adaptor are detected correctly and only one is connected. Normal in this case. Then I can ping my computer on the network that is wireless but I cant acces the net. THe laptop is on windows and connect to the net whit no problem. So I think I can rule out the modems. The problem I think is that I have 2 modems. D-Link DI-524 and Lynx 210 from starbridge. The Starbridge is auto program whit information to auto connect to my isp. Then I send the signal to my DI-524 to have wireless in the house. My pc was on win XP before and could connect whitout any setting. I think the computer can see the router but cant get to the lynx. Both computer have the same gateway to connect to. I'm also able to ping Ubuntu.com. Frankly I'm a bit unfamiliar whit linux and this is starting to confuse me. Mabe I should install the version before.

If you can help I will appreciate

---

### Post by Drate on 2007-12-14
Can you ping ip addresses?  If so you might try editing your card properties (system > admin > networking) and find hte tab to pu tin your dns server IP's.  This is just a suggestion, not sure if it'll work for you, but worth a try maybe?

---

### Post by technoplume on 2007-12-14
Yes that the strangest thing, I can ping web address and I get answers. But I can't get the web broser to load the pages. Also I tried 6.06 this morning and the problem is still there.

---

### Post by technoplume on 2007-12-14
YAY I found an answer that work. It turn out ivp6 is at fault

[http://ubuntuforums.org/showthread.php?t=87798&highlight=blacklist+ivp6](http://ubuntuforums.org/showthread.php?t=87798&highlight=blacklist+ivp6)

for others to find

---

