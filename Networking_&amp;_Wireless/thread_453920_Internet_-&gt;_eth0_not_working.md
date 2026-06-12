---
title: "Internet -&gt; eth0 not working"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by Eric the Red on 2007-05-24
I can connect via wireless with no problem. However, I can't connect with a cable. do you guys have any reason why that may be?? 

What troubleshooting tips should I follow?

---

### Post by jba6511 on 2007-05-24
same problem here. You can search for my thread if you want some help, but I still have not gotten it resolved.

---

### Post by rohan182 on 2007-05-25
i have the same problem, i have a realtek Gigabit adapter,

it was working when i first installed ubuntu a week ago and now it doesn't...

weird...

---

### Post by rohan182 on 2007-05-25
i have figured out my problem, i am on a dual boot system and when i wanted to use ubuntu instead of XP i just hibernated xp so loading times are shorter.. 

anywho, it weird but my wireless works even when XP is hibernated and i use ubuntu but my wired gigabit lan connection doesn't.

awell hope anyone in the same position as me found this helpful .:popcorn:

---

### Post by venome on 2007-05-26
same problem on my computer. I've been running Fiesty for few weeks now and out of nowhere, my eth0 stopped working. I haven't made any modifications to configuration files since last start, so I guess it shouldn't be my fault but some system error. I tried to disable eth0 auto configuration, disable roaming mode, tried static IP, none of it worked, it seems like the networking device does not run at all (i don't recieve response to DHCP IP request broadcasts, with static IP (correctly set) there is no response to the computer which responded yesterday with no problems). (I'm dualbooting Vista, there the network interface works (lspci says its Realtek 8139). Any suggestions?

---

### Post by rohan182 on 2007-05-27
> **venome said:**
> same problem on my computer. I've been running Fiesty for few weeks now and out of nowhere, my eth0 stopped working. I haven't made any modifications to configuration files since last start, so I guess it shouldn't be my fault but some system error. I tried to disable eth0 auto configuration, disable roaming mode, tried static IP, none of it worked, it seems like the networking device does not run at all (i don't recieve response to DHCP IP request broadcasts, with static IP (correctly set) there is no response to the computer which responded yesterday with no problems). (I'm dualbooting Vista, there the network interface works (lspci says its Realtek 8139). Any suggestions?

are you connecting to a router/other computer in which you can identify if there is a link at all? (on a router the LAN LED will light up) if there is a light and you have a DHCP configuration i found when i went to network settings i had to put a tick in the box next to my LAN wish i could get a screenie for u but im booted in xp at the moment. its the window where it says "roaming enabled" or something like that and the box next to you LAN will have nothing in it (no tick) put a tick in it. This only worked when i actually knew my network card was working (plugged it into my router directly and the "Link" LED was flashing. Hope you could actually understand what im talking about cause i dont think i would. feel free to PM me or something if u need anything.

Also as i said in a previous post are you hibernating when in vista? if so shutdown out of vista completely..

---

### Post by venome on 2007-05-27
> **rohan182 said:**
> are you connecting to a router/other computer in which you can identify if there is a link at all? (on a router the LAN LED will light up) if there is a light and you have a DHCP configuration i found when i went to network settings i had to put a tick in the box next to my LAN wish i could get a screenie for u but im booted in xp at the moment. its the window where it says "roaming enabled" or something like that and the box next to you LAN will have nothing in it (no tick) put a tick in it. This only worked when i actually knew my network card was working (plugged it into my router directly and the "Link" LED was flashing. Hope you could actually understand what im talking about cause i dont think i would. feel free to PM me or something if u need anything.

Also as i said in a previous post are you hibernating when in vista? if so shutdown out of vista completely..

Thanks -
I've read the post about hibernating, but I assumed then that when the network worked for me before (even when Vista hibernated), that the problem should be somewhere else. But it wasn't...I shut down the windows and out of the blue the Ubuntu network is back on again... I guess it might be because of the new network driver that microsoft / realtek released and that I updated to few days before.

---

