---
title: "dual wireless cards cause lockups"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by sanjochris on 2010-09-26
My laptop has only an internal wireless 'b' card, so I use a plug-in wireless 'g' in the pcmcia slot. There is also a wired ethernet port which I don't use at all.

When I boot up, the external card is configured as wlan0 and the internal card as eth1. Drivers appear to be appropriate (ath5k and orinoco).  But the cards won't co-exist, and if I don't turn off the internal card rapidly the machine will lock up. If it doesn't, it will as soon as I open a browser. I have to go to the connections icon and manually disconnect the internal card as fast as possible, after which all is fine.

I would rather not have to keep doing this, but I also don't really want to prevent the internal card from working at all. XP Pro on this machine was fine, running both interfaces without conflicts.

Is this something like an IRQ conflict, which I distantly recall from Wins95 days as being a constant hassle? Can I reconfigure one card so that both may live happily together?

If it helps the external card is an Atheros AE2413 chipset and the other is an Intersil Prism 2.5 Wavelan.

Thanks!

---

### Post by fooman on 2010-09-26
hello,  can't you just disable the internal card in the computer setup (bios),  when using the external card?

you can always re-enable it again when/if needed.  should be pretty simple to do and only take a few minutes to enable or disable.

---

