---
title: "Strange networking issue and it's resolution"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by SonicJMC on 2008-03-06
Didn't know where else to put this.
My Ubuntu box was having a networking issue where the wired internet connection would just fail for about 30 seconds at random intervals, effecting http, pop, and some other protocols, but NOT Pidgin.
I was tearing my hair out looking for the problem.

I went to my BIOS and enabled AMD's "Cool N Quiet" trying to solve something I thought was completely unrelated.
Now, with that turned on, my system's networking is rock solid. If I shut that BIOS option, I have networking problems again.:confused:
This also caused other issues, such as boot occasionally hanging on e-mail related daemons.

Processor: AMD Anthlon 64-bit x2
Mother: MSI K9 Platinum
Network:

Windows is NOT effected, just Linux. I've only tested this in Ubuntu.
This is almost as strange as my old Dell (In Windows, using "Auto Sense" on the network card made the 3D graphics card perform unusably slow, even after replacing the card with an expensive ATi)

So, if anybody has such a strange issue, try this!

---

### Post by chewearn on 2008-03-06
Looks like you might be having an unstable hardware, and could be due to overheating (not enough fan ventilation, etc).

If you really want to nail the problem down reliably, one way to do so is to run memtest for a few hours, see if any failure pops up.  Then, open up the PC case (optionally blow a table fan at it), run the memtest again and see if there is any improvement.

---

### Post by SonicJMC on 2008-03-06
It's not a heat issue, already diaged that.
Memory is fine, passes with flying colors.

---

