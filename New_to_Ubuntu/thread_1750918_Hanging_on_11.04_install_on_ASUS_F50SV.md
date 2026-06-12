---
title: "Hanging on 11.04 install on ASUS F50SV"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by hlruler on 2011-05-06
I'm completely new to the world of Ubuntu, but I'd been hearing nice things about it so I thought I'd give it a try. I downloaded the image file and extracted it as commanded, then proceeded with the installation to a fresh partition. Everything went smoothly until the computer rebooted, after which I selected Ubuntu to boot, and the comp simply hangs on "Completing Installation"

I tried the other Installation options, and I did manage to get it to boot that way, but after the installation completed, the computer rebooted again and afterwards I have been unable to boot Ubuntu at all. It either hangs on the generic, or in recovery mode after displaying some humbo jumbo about "Registered taskstats version 1"

After doing some research, I've found others have had trouble with ASUS laptops, but they all referred to older versions of Ubuntu, so I thought I'd ask to see if anyone would have a solution. Anyhow, thanks for the potential help!

---

### Post by hlruler on 2011-05-06
Just as an update to anyone who might be reading this, I attempted to install version 10.10, to no avail. It does the exact same thing and hangs up in the same places. 

Please help! And thanks!

---

### Post by VeRychard on 2012-04-17
I SOLVED IT!!!!!

If you have an Asus laptop, or you have this option in BIOS CHECK IT!!!!!

Go to bios >
Security> I / O interface Security> [COLOR=red]"New interface card"[/COLOR] or so. SET IT TO LOCKED!!! 

After that everything went fine for me ^^

Booted properly

Hope it helps :)

---

### Post by lukej2000 on 2012-09-24
> **VeRychard said:**
> I SOLVED IT!!!!!

If you have an Asus laptop, or you have this option in BIOS CHECK IT!!!!!

Go to bios >
Security> I / O interface Security> [COLOR=red]"New interface card"[/COLOR] or so. SET IT TO LOCKED!!! 

After that everything went fine for me ^^

Booted properly

Hope it helps :)

This exact tip helped me to boot a Gparted Live USB gparted-live-0.13.1-2 on a ASUS Pro61SL laptop.

---

