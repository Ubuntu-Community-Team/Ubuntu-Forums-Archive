---
title: "Ubuntu, LG R400, and Atheros AR5006X Wireless"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by Xas3r on 2007-09-03
Hello there,

I've tried to get my Atheros AR5006X Wireless Card to work now, for a couple of days. In this period of time, I've been trying a lot of different "solutions" to how I can get it to work. among those are madwifi and ndiswrapper. But nothing just seems to work, and it gets a bit frustrating, that no guides will want to work.

Could it be I got a complete different wireless card then my dual boot windows xp tells me? or for that matter a different chipset? It's hard to believe but probably possible.

lspci shows this:

[B]02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4353 (rev 15)
05:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)[/B]

And yes, it tells me I got another unknown device, named Marvell. But then again windows xp tells me thats the wired network, that means I'm using an unknown device to write this and search for answers.

dmesg shows nothing regarding wifi either.
iwconfig is also pointing out "no wireless extension".

Am I missing something here or whats the problem. I'm all out of ideas, and would really appreciate some help on this matter. thanks in advance.

Ohh and P.S. I couldn't install Ubuntu from the live CD, I had to use the alternate cd with text install. And thats because I got an ATI Radeon X2300 Graphic Card. And another thing, the restricted driver manager shows "Atherios Hardware Access Layer (HAL), Enabled and in use.

---

### Post by CL_FlushEntityPacket on 2007-09-04
i have the exact same problem, i have been totally unable to make it work with ndiswrapper nor madwifi, with ndiswrapper i load the "ar5211" driver that winxp is using and it just returns no hardware has been found maybe install was incomplete, and it doesnt work when modprob'ed

---

### Post by Xas3r on 2007-09-11
Please let me know, if you find the solution. Because it seems like I just can't find it. :confused:

Or for that matter, if anyone else got the solution. thanks.

---

### Post by feneks on 2007-09-11
Have had a look at [http://wiki.archlinux.org/index.php/LG_R400_Installation](http://wiki.archlinux.org/index.php/LG_R400_Installation) ?

It's Arch-Linux but perhaps peope there can help you.

regards
feneks

---

