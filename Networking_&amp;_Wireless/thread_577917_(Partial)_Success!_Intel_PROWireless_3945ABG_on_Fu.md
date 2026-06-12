---
title: "(Partial) Success! Intel PRO/Wireless 3945ABG on Fujitsu-Siemens Amilo Pro V3505"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by Humph on 2007-10-16
My hopes were so high when I ran the live CD of Gutsy Gibbon this evening. My wireless was actually detected and, glory of glories, my little LED was lit up and I could surf the interwebs and everything! Without hesitation I double-clicked the Install icon.

As with Dapper Drake and Feisty Fawn, for some reason the Live CD will only install on this laptop when started in Safe Mode -- it gets stuck at 15% and stays there forever. So a quick reboot later and, and, and, dammit! No LED, no wireless interface, no nuffink. :cry:

After some perusal I read about dmesg, which showed the Kill Switch was on, but could find no keycodes to turn it off (Fn+F10 should do it on my laptop, but it doesn't generate a keycode). What I found utterly perverse was that as soon as I booted to XP Pro the wireless activated again almost instantly. 

Some two hours of bashing my head against my desk later I thought, by way of a last resort, I'd visit [www.fujitsu-siemens.co.uk]("http://www.fujitsu-siemens.co.uk"). A couple of moments of faffing later I'm at the download page for my laptop, inspecting the list of BIOS updates available. In the notes for previous BIOS revisions I noticed this in version B0E:

> - Before login Windows, BIOS will still take responsibility of Wireless LED control.I'm now the proud owner of an orange LED that I can't turn off, but I'm very happy 'cos I've got wireless working in Ubuntu for the first time ever! :grin:

Edit: Dang, my sig doesn't work :(

---

