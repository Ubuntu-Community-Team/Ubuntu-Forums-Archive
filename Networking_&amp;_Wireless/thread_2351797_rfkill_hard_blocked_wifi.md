---
title: "rfkill hard blocked wifi"
date: 2017-02-06
forum: Networking &amp; Wireless
---

### Post by roppwer on 2017-02-06
Hi all,


First of all, I'm pretty new with Ubuntu, but before post it here I've searched in a lot of forums about my problem and I found some information, but in any case I could fix my laptop... 


Second, sorry about my English... 


Third, my system: My laptop is an Positivo n9480. Running Ubuntu 14.10.


Fourth, my problem: Everything works ok when I launch my laptop normally. But if I switch off my wireless connection, I can't switch it on again because is hardware blocked by rfkill.


It doesn't matter the way of switching it off and on again:
- Function key + F2
- sudo ifconfig wlan0 down & sudo ifconfig wlan0 up
- switch it off in the network menu (after switch it off it says that it is switched off by a physical switch, but it is false because my laptop doesn't have any physical wireless switch. I think that it says this just because it's hardware blocked).

---

