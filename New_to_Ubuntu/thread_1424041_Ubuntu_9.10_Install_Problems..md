---
title: "Ubuntu 9.10 Install Problems."
date: 2010-03-07
forum: New to Ubuntu
---

### Post by JDRMP on 2010-03-07
Hello,
First time Ubuntu user, I have zero knowledge of Linux.
 
I have been trying to install Ubuntu 9.10 as a dual boot OS on a Vista x64 computer using these instructions hxxp://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm.
 
First couple of problems I have encountered are:
 
1. When I "Try Ubuntu without any changes to your computer" It loads and my wireless mouse and keyboard work fine.  When I do an install I have to press F6 and check Apic=off or install will freeze on the first page where language is selected. By using Apic=off I can fully install Ubuntu but when computer reboots and loads Ubuntu and starts, the mouse and keyboard do not work. The only way to get out of Ubuntu is to disconnect power to the computer.  Booting into where the repair selection is just locks up the computer. Vista still boots and works ok.
 
2.  Screen resolution is way to large I to have guess what is on the bottom of the page and use the tab key hit or miss to move on to the next install page.  Resolution is still to large even when I "Try Ubuntu without any changes to your computer".Cannot be changed from 640 x 480 when I go into Settings>Display
 
The computer is a 
Gateway DX4720-03 Intel Pentium Dual Core E5200 2.50GHz
 
The Graphics Description:   Integrated Graphics  
 GPU/VPU:   NVIDIA GeForce 7100 
 
Thanks

---

### Post by switch10 on 2010-03-07
Don't cut power to your machine.  hold the power button until it shuts off.  

When you choose "try Ubuntu without making changes", have you tried installing from there with the desktop icon?

---

### Post by candtalan on 2010-03-07
When in the initial CD boot menu the F4 at the bottom of the screen can be useful to force the machine to use more traditional graphics.

I have had keyboard problems with use of a rather old keyboard which worked fine on some machines, but not with a particular type of mainboard. However, a newer keyboard worked ok.

good luck

---

### Post by JDRMP on 2010-03-07
> **switch10 said:**
> Don't cut power to your machine. hold the power button until it shuts off. 
 
When you choose "try Ubuntu without making changes", have you tried installing from there with the desktop icon?
 
 
Thanks
 
When it hangs the power button has no effect.  I can hold it forever and the computer will not shut off.
 
I did try to install like you suggest but same as before.

---

### Post by JDRMP on 2010-03-07
> **candtalan said:**
> When in the initial CD boot menu the F4 at the bottom of the screen can be useful to force the machine to use more traditional graphics.
 
I have had keyboard problems with use of a rather old keyboard which worked fine on some machines, but not with a particular type of mainboard. However, a newer keyboard worked ok.
 
good luck
 
 
Thanks
 
I have tried both my wireless mouse and keyboard and my ps2 mouse and key board with the same results. After install keyboard and mouse will not work.

---

### Post by JDRMP on 2010-03-08
Think I have found the problem.  When I go into Bios and set ACPI Aware O/S to NO I can boot up Ubuntu with no problems.  But, Vista will not boot up until I reset it to YES.
 
How do I edit the Ubuntu  boot.cfg file to turn off ACPI when Ubuntu boots up?
 
Thanks

---

