---
title: "Dual boot with Moblin"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by sleepy_yellow on 2010-05-01
i know there are probably a countless other posts about this, but i read a few and im such a noob that i cant even follow those instructions, i followed this guide first [http://www.garypigott.net/how-to-dual-boot-moblin-and-ubuntu/](http://www.garypigott.net/how-to-dual-boot-moblin-and-ubuntu/) which was good but it didnt really end the way it should have. i installed moblin as dev1 made a 4GB swap drive as dev2 then installed ubuntu UNR as dev3 both i think as MBR then rebooted and it booted up into UNR instead of moblin and when i want to boot up into moblin it says 
> vga=current is deprecated. Use set gfxpayload=text before linux command instead. 
error; couldnt read file
press any key to continue...

so then i tried to look where the vga=current file is stored at and i found its stored under /boot/grub/grub.cfg so i opened it up and edit vga to gfxpayload but i cant seem to save it so i been looking for commands to open it up in the terminal so ican edit it. i tried vi /boot/grub/grub.cfg and it opens up but now i dont know how to edit and save it i read i ahve press A to edit and qW to quit but when i press A it deletes to whole line.
am i even doing it right by editing the grub.cfg or do i need to do something completely different. 

please help.

---

### Post by sjosul on 2010-05-04
As a short-term fix, rather than edit grub in Ubuntu, while in grub, scroll down to the Moblin entry in the grub menu, and press "e" to edit. "vga=current" is the last string, just delete it and type in "use gfxpayload=text" and hit ctrl-x to boot.

As I say, it's a temporary fix, because you will have to do this every time you want to boot into Moblin.

Alternatively, using sudo you can actually make that edit to grub.cfg (I did it, and it worked fine), though it is not recommended.

---

