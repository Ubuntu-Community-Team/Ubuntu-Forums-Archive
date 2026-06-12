---
title: "Installation freezes before it starts...help?"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by Rithoy on 2010-03-10
Okay, so I pop in the CD, had it boot from the CD drive at start up, and select "Install Ubuntu" and it freezes right there. I can't change the option, I can't hit escape. After I hit so many buttons, the internal speaker starts beeping with each key press. I'm very confused and haven't found anything near this when I searched the web. Any help is much appreciated, thanks!

---

### Post by sikander3786 on 2010-03-10
> **Rithoy said:**
> Okay, so I pop in the CD, had it boot from the CD drive at start up, and select "Install Ubuntu" and it freezes right there. I can't change the option, I can't hit escape. After I hit so many buttons, the internal speaker starts beeping with each key press. I'm very confused and haven't found anything near this when I searched the web. Any help is much appreciated, thanks!

Do you have the Live CD? If so select "Try Ubuntu without making any changes to this computer"

See if that Ubuntu can start. Or the only thing I will recommend is to replace either the CD-ROM Drive or the CD itself. Might be the CD is not burned correctly. Try burning it in lower speeds.

Sikander.

---

### Post by JDRMP on 2010-03-10
I'm no expert on this but had the same problem.  At the menu "Install Ubuntu"
select F6, select turn off acpi, hit enter so it puts an x there, use the Esc button to exit out then do the install. If you are having this problem now you may need to go into your BIOS after the install and turn off acpi so UBUNTU does not freeze after it boots up. There is a way to edit files so acpi is turned off during boot so you don't have to go into the BIOS.  You will need to know if your version is GRUB or GRUB2 as editing for acpi=off is different for each.

---

### Post by juliobahar on 2010-03-11
> **Rithoy said:**
> Okay, so I pop in the CD, had it boot from the CD drive at start up, and select "Install Ubuntu" and it freezes right there. I can't change the option, I can't hit escape. After I hit so many buttons, the internal speaker starts beeping with each key press. I'm very confused and haven't found anything near this when I searched the web. Any help is much appreciated, thanks!

EXACTLY the same problem with me today. I tried Karmic LiveCD to install karmic on my old Toshiba (Satellite A55-S306) Centrino 1.6MHz intel, 512mb with an intel builtin graphic card. I couldn't figure out what the problem is. The CD looks fine. The CD/DVD writer reads the LiveCD well. Windows XP runs perfectly. 

Only after booting from the CD and choosing either "install ubuntu" or "try ubuntu without changes" the screen will freeze at the selection menu and the CD spins up then down after a couple of seconds. Pressing ESC will freeze the computer completely and a beeping sound from the internal speaker shouts on each key strike. Yet I can still restart by Crtl+Alt+DEL. 

I've tried modifying all the boot up options on F6 and F4 but none seemed to help.

I wish I can boot using a pendrive. But my laptop is old - doesn't have a USB booting option -

---

