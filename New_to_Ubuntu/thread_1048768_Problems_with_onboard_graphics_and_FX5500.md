---
title: "Problems with onboard graphics and FX5500"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by iamaperson on 2009-01-23
I recently got my computer to dual book Windows XP and Ubuntu. I had alot of trouble installing using the Nvidia GeForce FX5500 but had no problems when it was not physically installed. After alot of messing around I got Ubuntu to use my FX5500 installed in a PCI slot. The only problem is when I go into my BIOS and disable the onboard Ubuntu ends up not starting up completely but when my onboard is active the computer will start boot ubuntu and it will switch displays to the FX5500. The problem is I don't want to have 2 monitors hooked up just so I can choose my operating system. Does anyone have any suggestions on what to try?

---

### Post by Rim on 2009-01-23
Can't u just set the priority? For example i have a 7050 onboard and a 9800GT in the pcie slot. In bios i set it as follows: Pcie first then the on-board GPU. So any os running will use the one in the pcie slot by default and leave the on-board.

PCIE->GPU for 9800GT

GPU->PCIE for 7050 onboard

---

### Post by iamaperson on 2009-01-24
That basically what I do. I change my bios to boot using the FX5500 instead of the onboard but Ubuntu will not start it always locks up with a blank screen after the usplash screen.

---

### Post by Rim on 2009-01-24
Hmm, then its a videocard issue. Have u installed at first the proprietary drivers for the onboard and activated them? If so i could try deactivating them and going back to the open source drivers. Then switch back to the other card in bios and load Ubuntu. Hopefully it will start, then u can proceed to getting the proprietary drivers for that and activating, then restarting.

:P much as urself i'm new to this but not to fideling around with windows and hardware. Give it a shot and report back here, if it still doesn't work i'll ask one of my friends for help and get back to u :)

---

