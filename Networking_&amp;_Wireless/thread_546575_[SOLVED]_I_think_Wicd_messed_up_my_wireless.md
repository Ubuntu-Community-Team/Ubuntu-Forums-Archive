---
title: "[SOLVED] I think Wicd messed up my wireless"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by Amablue on 2007-09-09
Just in case it's important, I'm using a Dell Insiron 2200 dual booting Ubuntu and XP.

I had trouble connecting to the wireless network with Network Manager so someone suggested I try Wicd. I tried it and it worked for my school network, but it doesn't work at all anymore. When I got home I couldn't see any access points. I reinstalled it a few times, I tried putting Network Manager back, I did everything I could think of, but now I can't get online at all. The software sees the wireless card just fine, but it just doesn't see any access points when I pull up the list. I can still use a ethernet port just fine though.

Here's the kicker though, when I boot under windows now I have the same problem. It can't see any wireless networks anywhere. Could Wicd messed up the wireless card at the hardware level or something? It doesn't seem like that should happen. Is it just a coincidence that my wireless crapped out on me? More importantly, anyone have any idea how to fix it?

---

### Post by ugm6hr on 2007-09-09
> **Amablue said:**
> I had trouble connecting to the wireless network with Network Manager so someone suggested I try Wicd. I tried it and it worked for my school network, but it doesn't work at all anymore. 

Here's the kicker though, when I boot under windows now I have the same problem. It can't see any wireless networks anywhere. Could Wicd messed up the wireless card at the hardware level or something? It doesn't seem like that should happen. Is it just a coincidence that my wireless crapped out on me? More importantly, anyone have any idea how to fix it?

Can't see how any software (Wicd included) could be the culprit.  Especially with the similar effect on Windows.

Suspect it's a hardware issue.... perhaps consider getting a new internal wifi card.  The Intel 3945 cards are pretty cheap.

---

### Post by walkerk on 2007-09-09
Yes, this sounds like a hardware problem. WICD is software run in Linux and would have no effect on your wireless capabilities in Windows..

If your wireless NIC crapped out your ethernet NIC would still work.. two seperate peices of hardware.

---

### Post by Amablue on 2007-09-09
> **ugm6hr said:**
> Suspect it's a hardware issue.... perhaps consider getting a new internal wifi card.  The Intel 3945 cards are pretty cheap.

Can you even do that for laptops? I didn't think you could just swap out parts like that.

---

### Post by Amablue on 2007-09-09
Nevermind, figured it out. Someone on the Wicd forum suggested that I had maybe hit Fn+F2 which toggles the wireless. I'm pretty sure I did; when I installed Wicd the first time I was testing it out so I used Alt+F2 to open a run prompt to run the tray applet; but at the time I coudln't remember if it was Alt+f2 or Ctrl+F2 so I just started spamming button combinations until the window appeared. I must've hit Fn+F2 in my button mashing. For some reason this affected both windows and ubuntu, so it must deactivate it on the hardware level or something. 

Anyway, it works now under both.

---

