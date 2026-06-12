---
title: "Fresh install stuck at blinking white line"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by c0d4041292 on 2010-05-26
I just Installed Ubuntu 10.04 and after install was completed when I restarted it, it just stops at the blinking white line after bios.

---

### Post by Ozymandias_117 on 2010-05-26
Try rebooting and hold shift as soon as BIOS has finished POST.

Edit: What I'm trying to see here is if you get into the GRUB options to find out if the problem is with GRUB or Ubuntu

---

### Post by c0d4041292 on 2010-05-27
> **Ozymandias_117 said:**
> Try rebooting and hold shift as soon as BIOS has finished POST.

Edit: What I'm trying to see here is if you get into the GRUB options to find out if the problem is with GRUB or Ubuntu

Holding shift does nothing

---

### Post by Xezus on 2010-05-27
what computer and graphics card are you using?

---

### Post by c0d4041292 on 2010-05-27
> **Xezus said:**
> what computer and graphics card are you using?

custom built computer:

Asus p5k3 deluxe
Intell e8400 @ 3.00 Ghz
Nvidia XFX 9800 GT
1 WD 1TB hdd
2x (idk brand) 1TB drives in Raid 0 for storage

---

### Post by c0d4041292 on 2010-05-27
I think I figured it out....I think it installed the bootloader on the wrong disk.... is there a way to change this without reinstalling?

---

### Post by Xezus on 2010-05-27
are you using grub?

---

### Post by c0d4041292 on 2010-05-27
> **Xezus said:**
> are you using grub?

Yes, I am using Grub

---

### Post by Xezus on 2010-05-27
you should be able to through your other os. i haven't personally used grub because i hate windows, but i think this might help you : [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by vikingstork on 2010-05-27
I have the same problem, i went on Launchpad to post it, and there was this writing on the page, so i read it and it has links and it led me to Boot troubleshooting section, and they say it's a fairly common problem -- it loads the splash screen, and splash screen goes away, and everything stops. They say, usually if you just delete word "splash" at the end of the line in "menu.lst", it usually fixes it. But when i tried to do it, i couldn't do it, the cursor sits in bottom left corner of terminal screen, and won't move, and i donno how to get it to do anything. So maybe some brave soul who actually knows the intricacies of command line editing, could try it. Or tell me, how to make the cursor to work and i will try it (it always worked for  me before). 
I am new to this, and the manuals and help screens are of no use, they all seem to assume that cursor always moves.

---

### Post by jamesgrant on 2010-12-19
try pressing insert to tell it u want to edit it

---

