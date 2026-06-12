---
title: "Grub Does Not see Keyboard"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by Romin-1 on 2007-11-08
I posted this query in Absolute Beginners about 24 hours ago and got no replys, so I thought I'd try in this forum.

> Yesterday when I tried to boot up my dual boot machine, which is on a home network, it froze on the window where you chose which OS to use. There was no 10 second delay, just the choice and this message: "304 Keyboard or system error". It had worked for the past several weeks. The only way I could boot at all was by plugging an old KB into the PS slot and hitting enter, then unplugging it. Once it had booted into Feisty everything was fine.

MY setup: Dual boot XP/Feisty, stand alone Gutsy and stand alone Vista, all on a wired network.

Seems as if the boot screen doesn't know I have a KB installed.

Any ideas on why this odd behavior and what to do?

I know this may seem a little odd, but if the fix has to do with going into bios I will need a refresher on how to get there. Having a senior moment here.

Many thanks,

Jon

---

### Post by Ehtetur on 2007-11-08
I'm guessing that it's your USB keyboard that give the 304 error and your ps/2 does not...

Lot of ways to get into the BIOS... Give a try to pressing the DEL key or F1 key...
If that don't work, boot up while you're pressing down the spacebar... that'll get the BIOS' attention.

When you're in the BIOS, enable USB support on POST... that should whack the 304 error

---

### Post by Romin-1 on 2007-11-08
Thanks for the suggestion, Ehtetur.

USB support was enabled in Bios. I'm thinking the KVM switch is somehow messing this up. After I click 'Enter' with the ps/2 and it opens up Ubuntu the USB keyboard works like a charm. This only happens on boot, not when switching from one PC to another. The Vista machine is acting as the home network server, not the Ubuntu one.

'Tis a mystery to me...

Jon

---

