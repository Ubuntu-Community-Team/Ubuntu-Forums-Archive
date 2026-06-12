---
title: "motherboard"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by hatridge on 2010-01-09
**[[B]Hewlett Packard Pavilion 610**]("http://www.dealtime.com/xPF-Hewlett-Packard-a610n-Pavilion-Desktop-PC") installed ubuntu 9.01 Works great except can not access internet. Had same proplem with windows xp on this machine. Intigrated motherboard may be toast however I would like a second opinion... how can I test?
[/B]

---

### Post by laidback on 2010-01-09
I would put another NIC card into one of the spare slots. If you don't happen to have one they're very cheap to buy. Or borrow one from a friend.

This assumes you're happy to take the case apart and understand the m/b layout etc.

---

### Post by Bartender on 2010-01-09
+1  Old NIC cards are dime a dozen, just about anything should work.

---

### Post by cascade9 on 2010-01-09
You can check the 'lights' near the ethernet plug- normally they light up if the ethernet is working. (sorry, tired to find a pic of this but its not as easy as I thought it would be). No lights _probably_ means 'broken ethernet' or possibly no signal due to broken cable. 

I'd try a different cable..and if that fails, like the others have posted, network cards are really cheap now.

---

### Post by hatridge on 2010-01-09
Thanks everybody, cable is fine as I'm on a different machine getting help with a friends pc. Linux works great for me, so much so that I have talked this friend into installing it on the  computer mentioned above. With mine Ubuntu found everything automatically ... opened up browser and was hard wired immed... but with this pavilion I can't seem to connect....I can't send a ping, nadda. I don't know if its a motherboard problem but I thought it might be. Am I missing something?. Are these motherboards not intgrated where I would have to replace the whole board? I opened up the back ....not comfortable with hardware other than slapping in some RAM or minor stuff. Any sugestions? Could I slap a Nic card in a slot and it would over ride the one intigrated to the motherboard? (cable plugs in at back of machine to this pencil sharpener sized block attached to motherboard) Also on one of the M\b slots there is a D-Link. Looks like a NIC but ethernet cable will not fit in it. Sorry I'm so green.

---

### Post by hatridge on 2010-01-09
Solved, replaced Nic...linux found it on first boot. Too easy! Thanks again:D

---

### Post by cascade9 on 2010-01-10
> **hatridge said:**
>  Are these motherboards not intgrated where I would have to replace the whole board? 

Snip!

Also on one of the M\b slots there is a D-Link. Looks like a NIC but ethernet cable will not fit in it. Sorry I'm so green.

Well, you've figured out that even with intergrated motherboards, even if something fails you can normally just use a PCI or-PCI-E card and get that function back again. Congrats ;)  

That 'other' D-Link card is probably a modem card. Personally, I'd remove it (and go into BIOS and turn off the network card that isnt working). Not that you have to, but I always figure that turning off or removing stuff you dont use or need cant hurt, and may make your computer boot faster and run slightly better. 

Not that you have to do that, but IMO its worth the 5-10 minutes it takes to remove a non-used PCI card and turn off things in the BIOS.

---

