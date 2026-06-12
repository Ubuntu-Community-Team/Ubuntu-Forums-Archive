---
title: "New Network Card, now Ubuntu Won't Boot"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by Rudy246 on 2006-10-03
Hello all, it appears I've run into more problems concerning networking in Ubuntu 6.06. 

I installed Ubuntu 6.06 Dapper Drake about 2-3 months ago on my computer, now it dual boots with Windows XP Home and Ubuntu. I was never able to get my old wireless network card to work with Ubuntu, so I was never able to get online. I tried everything suggested by various Linux-savvy friends, but to no avail.

I looked online, in various places, to try and find a solution, and the only one I could find was that my  wireless network card was not compatible with Ubuntu. So, I just got a new router / wireless card combo over the weekend. The router is a Linksys Wireless-G, the wireless card is a Linksys Wireless-G PCI Adapter. I asked the employee at the store I bought the two, Best Buy, if the card was compatible with Linux, he said that he had personally gotten it to work and connect to the Internet under Linux. So I figured it would work out fine. Apparently I was wrong.

I installed the router and wireless card last night, I got everything set up nicely, and everything went smoothly. The wireless works fine under Windows, but I can't say the same for Ubuntu. I booted in Ubuntu and changed the network settings to the new configurations of the router and wireless card, but nothing changed, it still wouldn't connect. I changed the network settings some more, but still nothing.

Now comes the really bad part. I booted up in WinXP to talk to a friend to ask for some advice as to what to try, then I rebooted so I could get into Ubuntu. I chose Ubuntu at the Dual Boot screen, and Ubuntu began to load. When Ubuntu showed "Configuring Network Settings" (or something to that measure), it froze. I sat and waited to see if it would continue booting, but to no such luck. I hit Enter on the keyboard, nothing. I had to turn the computer off via the button on the machine.

I tried booting up in Ubuntu again, only to have the same thing happen. I gave it about 10 minutes, and eventually the screen changed to nothing but text. The screen was black with just rows of white text. It was like a text version of the graphical boot screen. It had lines such as:

Loading Interace...........................OK

Etc. But when it got down to "Configuring Network Settings", it had no "OK" next to it. I hit Enter on the keyboard, and several rows of text came up, none of which I understood. I took down one line of text:

atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.

I attempted to type in 'setkeycodes e001 <keycode>' in an empty line when it allowed me to type, but every time I would get past "set", it would auto-enter, so I couldn't type the entire line.

So now Ubuntu will not boot for me, and even if it did, I don't think the network card would change the fact that it won't get online.

Any help would be greatly appreciated, as I am stuck in a dilemma that I have absolutely no clue as to how to get out of.

-Rudy

---

### Post by zaniness on 2007-10-22
Here's another thread about your problem: [http://ubuntuforums.org/showthread.php?t=233913](http://ubuntuforums.org/showthread.php?t=233913) . Hope you'll solve it!
Cheers

---

