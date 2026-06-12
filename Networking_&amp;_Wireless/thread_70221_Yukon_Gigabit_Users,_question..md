---
title: "Yukon Gigabit Users, question."
date: 2005-09-29
forum: Networking &amp; Wireless
---

### Post by Mr. Electric Wizard on 2005-09-29
Simple question.
Of the people using the Marvell/Yukon gigabit cards, any flavour of them, does anyone have their card working when connected to a gigabit switch/router.

My card worked fine when hooked up to a 100Mb Router, _but will not work when hooked up to a gigabit switch._

I am contiplating opening another bug report.
I need to know who has their Yukon card working when connected to a gigabit switch/router, and the model number of the card, and said router/switch.

Thank you.

---

### Post by kleeman on 2005-09-29
What exactly goes wrong? You said in another thread that it works with a 100Mb router so I assume the driver loads OK (sudo modprobe sk98lin). Does the dhcp step screw up?

---

### Post by Mr. Electric Wizard on 2005-09-29
Hooked up to a 100Mb router works fine.
I took this router out of my network and replaced with a 1,000mb switch.
Right after I replaced the router with the switch, my Yukon card would not do anything...
That's why I am asking if anyone else has hooked one of these cards to a true gigabit network, and got it working.
It works fine, and has always worked fine, on a 100Mb network.

What I am wondering, and I'll test today at lunch, is if one of the wires on my network cabling is bad (not connected) then that _might_ tell why it works in 100Mb mode, and not Gigabit mode...

---

### Post by Mr. Electric Wizard on 2005-09-29
YEAH BABY!
It was a cable issue!


Here's the deal.  When you have 100Mb connection using Cat5 cable, you are only using 2 pairs of wires, and the other 2 pairs are not used.  But in gigabit configuration, all 4 pairs are used.  So, when I had this card plugged up to a 100Mb router, it worked fine because all the wires that 100Mb needed to function were there.  But, when I changed the 100Mb Router to a 1,000Mb Switch, one of the wires was not connected.  DOH!
So I plugged the last wire in and VOILA it started working!
:D :D :D 

Kleeman and everyone else that has helped, thanks for all your help, seriously!
:razz: 

I will post this in the other Yukon thread also!

Thanks again!

---

