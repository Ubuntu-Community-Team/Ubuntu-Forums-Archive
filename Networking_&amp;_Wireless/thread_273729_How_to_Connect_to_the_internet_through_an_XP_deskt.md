---
title: "How to Connect to the internet through an XP desktop?"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by Fansler on 2006-10-08
I have a wireless router, and I have a computer running windows XP home edition connected wirelessly to it. I have another computer with the latest version of Ubuntu installed, but I have no wireless card. What is the procedure for setting up an internet connection through the windows XP computer for the one with Ubuntu?

---

### Post by spd106 on 2006-10-09
Do you have a crossover cable or a hub?

A crossover cable will allow you to just plug the cable into both network cards (NIC). If you don't have one then you should use a hub and two normal (straight through) cables. Depending on your hardware you may be able to use a straight through cable instead of a crossover, though most NICs won't do this.

On XP you will need to enable ICS (Internet Connection Sharing), I'm not sure exactly where the option is but it shouldn't be too difficult to find. Then simply plug in the cables.

On Ubuntu open Sytem -> Admin -> Networking and check that your card is set to dhcp, it should work automatically.

---

