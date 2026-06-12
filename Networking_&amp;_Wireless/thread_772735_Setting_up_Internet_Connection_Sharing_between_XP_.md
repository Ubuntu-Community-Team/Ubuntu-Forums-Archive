---
title: "Setting up Internet Connection Sharing between XP and Hardy"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by michaeless on 2008-04-28
I cannot get Internet Connection Sharing to work properly between my XP machine(which has the two interfaces) and my Hardy machine. 
My XP machine has the two network cards, one wired(internet) and one wireless(the Ad-Hoc network).
I can see the connection "sharedinternet" on both machines and can connect to it. The IP of my XP machines wireless card is 192.168.0.1 and using manual network configuration on my Hardy box, I set the IP to be 192.168.0.2 and the gateway to be 192.168.0.1. I can't figure out why I am unable to ping the XP machine from my Hardy box and the network isn't working at all.
Will anyone that has done this before help me out here? It's the first time I have tried setting up ICS.

Thanks in advance.

---

### Post by chicoharv on 2008-04-28
I beliee your trouble is with your IP addresses. I have a gateway and its address is 192.168.1.254. I have 2 PC"s one with XP and one with Hardy and two wirless laptops. The gateway assigns the addresses for my computers, I hope yours has a automatic mode then you won'thave to worry about assigning addresses. My laptops use the same address weather they are wired or wirelessAll address are the same except for the last group. My computers have been asigned .68,.64,.65,.69. I believe yout gateway and your dual connection computer need differenrIP address and it may have configured your Hardy with a different address you are trying to assign. When I upgraded to Hardy everything worked automatically except I can't network print from the Hardy to my printer which is on my PC withXP. Before I  upgraded everything worked.In short, try lettijng your gateway set the addresses automatically. You may have to delete your network  in the Hardy  but I don't think so. If you have a printer on the windows network and your Hardy prints to it please let me know how you got that working.

---

### Post by michaeless on 2008-04-28
Here's my current setup that I am trying to get working, there's no access point(wireless router) in the setup. Is it possible to get it working?

---

