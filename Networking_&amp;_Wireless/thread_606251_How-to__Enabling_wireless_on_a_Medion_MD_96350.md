---
title: "How-to : Enabling wireless on a Medion MD 96350"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by ZarathustraDK on 2007-11-07
Heya,this problem had me annoyed for quite a while. I had just purchased a new laptop, the Medion "Akoya" MD 96350 from Aldi (a german supermarket-chain who puts out these laptops once in a while). Everything worked when I installed Ubuntu on except (drumroll) wireless and a few other bits.

I wasn't worried though, I knew from these forums that intel hardware is pretty well supported on linux, so it was one of those "oh well a little tinkering will fix that"-state of minds I found myself in.

This quickly changed though, as this piece of hardware had an ominous behavior at best. It was there in lspci, it was there in lshw, the drivers were installed, but it didn't show up in network manager or using iwconfig.

Here is what is wrong with the thing :
The Medion MD 96350 has a wireless kill switch which, when on, has the wireless card turned off. Laptops usually have the kill switch readily available as a push-button somewhere on the chassis, NOT the MD 96350, nooo nooo it's SPECIAL. This particular laptop has some kind of fancy Ipod-like multimedia pad (they're like buttons with play, stop, backward and forward buttons, and, you guessed it, the wireless kill switch. This would have been all nice and dandy if they just worked which they don't (drivers are very esoteric and not available for linux). BIOS was a joke since wireless lan it had two options : "Disabled" and "Last state" (which also was, yes, disabled) So basically the multimedia pad was holding my wireless hostage.

I tried the acerhk package to no avail, modprobed anything with asus in it to see if the panel would lit up, which it didn't.

So the solution to this problem is as follows :

- Temporarily sell your soul and install Vista which came with the laptop (don't worry, you'll get the option of getting it back in the end).

- In Vista : Install the "Multimedia panel" and "Launch Manager"-drivers from the device driver cd which came with the laptop. (Launch Manager is the most important as that's what activates the craved wireless-switch).

- In Vista : Un-block your wireless with your newly-aquired kill/revive wireless switch. It should light up and give of some sound if it works.

- Don't touch the switch again if it's on.

- Reboot and eliminate Vista, reclaim your soul, you got wireless in Ubuntu now.

Again, this is very specific to the MD 96350, but I guess the same problem could be thought possible on other laptops, so here's the run-down of the general tactic :

You got no wireless, and it's because the kill switch is on. You got no access to the kill switch as the button to the switch requires windows drivers. Solution : install windows, install the drivers, turn on the wireless, problem solved.

It seems really trivial in retrospect, but the weird sense of having the wireless card "right there in front of me installed and detected", had me spending many nights on irc, forums and whatnot searching for a solution, don't let it happen to you ;-)

---

### Post by fgross2 on 2007-11-17
I couldn't believe it but it works! :) 
Thank you very much for this useful hint.

---

### Post by totk on 2008-01-14
Hello I got the same laptop, you are right the WiFi problem is annoying, however I have another problem, which appears to be even more mysterious ( at least to me):
My laptop won't boot properly after using Ubuntu (or any other linux even from a live disk). It powers down before it reaches the BIOS boot then turns it self back on again and  then boots properly :?: 
I have already posted a question on it but didn't get a reply so far.
[http://ubuntuforums.org/showthread.php?p=4128966#post4128966](http://ubuntuforums.org/showthread.php?p=4128966#post4128966)
Have you got the same problem? 
If so what did you do about it?

---

### Post by YannickB on 2008-04-09
Hello all, I (dundundun) have the same laptop, bought from ALDI aswell, I always used windows so I didn't have the same problem posted here, but I now wanted to switch to Ubuntu & after a bit of a hassle to install it, I find out that my wireless connection doesn't work.

He can actually receive the wireless signals, I can choose the networks to connect to, but the connecting always fails, while I'm 100% sure I'm using the correct passphrase.

Current Ubuntu version installed is the 7.10
If anyone could help me out I'd be very grateful! :P But beware, I'm a complete Ubuntu/linux Newbie, so do it in Layman's terms please :D I found quite some replies to similar problems a bit confusing ;D

Grtz,
Yannick

---

