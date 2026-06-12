---
title: "signal strenght much better with windows"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by deadguy87 on 2007-05-15
I have a Atheros ar5006eg wireless card. It works in Ubuntu Feisty Fawn, but It was always reporting a weak signal. I wasn't sure if it was correct but I tested it by anti-war walking. To see how far the signal would go. When it dropped out I booted into windows and could pick up the signal loud and clear. I walked another 300 feet before It dropped out again. Is there a fix for this becuase there is a park near by that I can be at and connect to when I use windows and would like to use Ubuntu there.

---

### Post by mengfei on 2007-05-16
Yeah, same here man.

Atheros on a THinkpad R40.

Can't figure out why it's such a crappy reception under Ubuntu though (nothing against Ubuntu).

I would like to go back to XP for convenience... but my new year's resolution was no pirating :lolflag:

Still holding strong!

(haha, although having 2 gigabytes of RAM and 120gb hard drive isn't helping at all - so tempting to switch back).

---

### Post by mengfei on 2007-05-17
BTW, I read somewhere that Atheros doesn't work so nice under Feisty Fawn.

Have you tried Edgy? Just a thought.

---

### Post by jonallport on 2007-05-17
Hi Guys,

Sorry I can't help with the range thing, I just wanted to comment on mengfei's remark about Edgy/Feisty.  I found the opposite to be true; I had no end of trouble connecting my notebook w/atheros card to WiFi if there was encryption turned on, since I updated to Feisty it's been running like a dream.

TTFN
J

---

### Post by hardyn on 2007-05-17
I have read something about this...

Its just fine, bu there is a numbers problem between network manager and the driver, it works just as well, but the level reports incorrectly.  there is a fix for it, but i believe it requires recompiling the driver.

I would post the article, but i don't recall where it was, im sure its googleable

cheers.

---

### Post by deadguy87 on 2007-05-18
it's more then just a reporting error. I've tested it and Ubuntu just doesn't go the distance.

---

### Post by mengfei on 2007-05-23
Hey deadguy87, give this a shot

[http://ubuntuforums.org/showthread.php?t=398144&highlight=thinkpad+r40](http://ubuntuforums.org/showthread.php?t=398144&highlight=thinkpad+r40)

This guy removed his network-manager.

Sure you won't get a fancy interface to connect wirelessly, but if it works, hey, what does it matter then?

Good luck!

I'll probably be giving this a shot too.

---

### Post by bmagyarkuti on 2007-05-26
I have the same problem with a fujitsu-siemens laptop. Don't try edgy, that won't even recognize the card.

---

### Post by Richard Goblin on 2007-05-26
Same goes for my Linksys WPC54GS card.  Under windows, I get 75%-80% signal strength from my couch, under Ubuntu I get 45%-60% signal strength.  I wonder if it is an issue with ndiswrapper ...

---

### Post by bmagyarkuti on 2007-05-27
Definately not ndiswrapper: the bug is also present with the madwifi drivers.

---

### Post by bmagyarkuti on 2008-06-06
This wonderful guy called yammosk has found a [fix for our range problem]("http://ubuntuforums.org/showpost.php?p=3444660&postcount=24").

It is just the following two commands entered to a terminal:
$ sudo modprobe acerhk autowlan=1
$ echo 1 | sudo tee > /proc/driver/acerhk/wirelessled

---

