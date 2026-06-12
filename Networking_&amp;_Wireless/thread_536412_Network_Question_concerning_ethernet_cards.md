---
title: "Network Question concerning ethernet cards"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by American_Outcast on 2007-08-27
I have two Ethernet cards on my Computer. I am running Ubuntu 7.04. All I want to do is have one of the Ethernet cards going to another computer so I can access that computer and remotely run it, etc. How do I set up Ethernet card two for this?

I apologize if this has already been asked. I am busy today and can't research this as much as I would like to.

Thanks

---

### Post by ddrichardson on 2007-08-27
You need a crossover cable. You can then setup addresses and IPs.

---

### Post by American_Outcast on 2007-08-28
I have an Ethernet cable going from the second card to the remote computer. Is that all I need? Then after that do I just assign a static IP address through the network tools in Ubuntu? I want this remote computer to be accessed only from a local network, being the second computer. I want it to be able to access the internet but only through my main, Ubuntu 7.04, computer. I will have XP on the remote computer, putty, etc.

---

### Post by ddrichardson on 2007-08-28
No a standard ethernet cable is different. You can change it - but you need crimping tools, it's easier to buy an ethernet crossover cable.

---

### Post by American_Outcast on 2007-08-28
Ok. Thanks. I was going to use an older computer for this but I am running into some hardware issues. No big deal, I know what the problem is. I just can't work on it right away. In the mean time I will check out the Ethernet crossover cables.

---

### Post by netztier on 2007-08-29
> **American_Outcast said:**
> Ok. Thanks. I was going to use an older computer for this but I am running into some hardware issues. No big deal, I know what the problem is. I just can't work on it right away. In the mean time I will check out the Ethernet crossover cables.

If the NICs on both computers are 10/100/1000 Mbit/s cards, there's no need for a crossover cable.

"Auto-MDI/MDI-X" (auto-crossover) is a feature in the 1000baseTX specs - you just need a cable that actually has 8 wires (4 twisted pairs) in it - as you need it for Gigabit anyway. You *can* use a crossover cable, but you don't have to.

If just one of the NICs is 10/100Mbit/s, you're better off with a crossover cable from the start.

best regards

Marc

---

