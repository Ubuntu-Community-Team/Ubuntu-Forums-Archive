---
title: "Wifi problems?"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by TheDoctorsCompanion on 2009-02-12
Anyone else having Wireless problems?

I am. Any ideas how to fix this darn thing? Already fixed it once before, but it's not working again for some reason.

OS: Xubuntu 8.10

Wireless Router/Modem: Belkin G 2.4Ghz hooked to Westell VersaLink Model327W

Support: Atheros 802.11 Wireless LAN cards

Info: I shut my laptop off one day and when I turned it on again, the wireless stopped working. Also, this was after I finally finished all my updates (for some reason they kept not working, then they all finally were installed and after that the wireless stopped working). I have a built-in Wireless Card to my computer (Acer Aspire 3680).

---

### Post by trikster_x on 2009-02-12
Did you have to build drivers from scratch?  Such as madwifi?

It could be that a kernel update messed them up a bit.

---

### Post by lkraemer on 2009-02-13
TheDoctorsCompanion,
while the GRUB menu is being displayed, use the arrow keys to cursor
down to the previous Kernel and boot from that.  This will get your
Wii working again, until you can figure out what method you used to
get your Wifi working.

You most likely use madwifi, and just need to recompile the module.

You need to figure out what you used to get it working the first time.
Then follow those instructions for a Kernel update.

lkraemer

---

