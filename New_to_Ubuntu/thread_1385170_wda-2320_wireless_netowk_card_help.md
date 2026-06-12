---
title: "wda-2320 wireless netowk card help"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by atuzyk on 2010-01-19
im running xubuntu 9.10 which i have upgraded from 8.04. my network card worked 100% until i restarted with the a fresh upgrade to 9.10. i noticed that ubuntu used restricted drivers before on 8.04 till 9.04 for my car, but after i upgraded it no longer uses them when I click on the hardware menu option. I know that my card works i just need some help getting it going. ive already tried searching on the forum many times and have come up empty. could it be because of hal depreciation? help me please!

Thank you!

---

### Post by Mark_in_Hollywood on 2010-01-30
I have a WDA-2320 card. I did a clean install of Karmic. 

I'm a former electronics tech. I suggest doing the following:

Turn the power to the computer off.

Remove the power cord.

Open the computer's case. Carefully remove the antenna from the wifi card. Next, remove the card. You will need a Phillips head screwdriver for this. Carefully remove the screw, making certain it doesn't drop in case or on the motherboard.

Gently pull the card from it's slot. Using a business card, gently wipe the gold "fingers" at the bottom of the card. Wipe both sides.

Reinsert the card. Return the screw to its position to secure the card. Put the cover(s) back on the computer, screw the antenna back into the back of the card, carefully. Don't overtighten.

Put the power cable (and all others) back into the box. Fire it up. If that solves your problem, please mark this post as solved. Otherwise, you may have to try your card on another box or another card on your computer.

---

### Post by A&#11375;A on 2010-01-30
> **Mark_in_Hollywood said:**
> I have a WDA-2320 card. I did a clean install of Karmic. 

I'm a former electronics tech. I suggest doing the following:

Turn the power to the computer off.

Remove the power cord.

Open the computer's case. Carefully remove the antenna from the wifi card. Next, remove the card. You will need a Phillips head screwdriver for this. Carefully remove the screw, making certain it doesn't drop in case or on the motherboard.

Gently pull the card from it's slot. Using a business card, gently wipe the gold "fingers" at the bottom of the card. Wipe both sides.

Reinsert the card. Return the screw to its position to secure the card. Put the cover(s) back on the computer, screw the antenna back into the back of the card, carefully. Don't overtighten.

Put the power cable (and all others) back into the box. Fire it up. If that solves your problem, please mark this post as solved. Otherwise, you may have to try your card on another box or another card on your computer.

I'm not inclined to believe it's a hardware issue, sounds more of a driver issue.

If you go to System>Administration>Hardware Drivers does it find anything pertaining to Wireless? 

You may need to activate the proper driver for your card.

---

