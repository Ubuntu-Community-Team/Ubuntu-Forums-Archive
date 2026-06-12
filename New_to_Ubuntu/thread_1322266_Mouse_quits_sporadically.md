---
title: "Mouse quits sporadically"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by aPaSv5 on 2009-11-10
Ever since I upgraded my motherboard, fan, CPU, and RAM, my mouse has been quiting sporadically -- regardless of what I'm doing, my mouse cursor will just freeze in place, at which point I will still be able to use my computer (i.e., none of the software will freeze) but mouse input will be totally ignored. Pressing Shift+Alt+NumLock allows me to control my mouse cursor with the number pad, however, trying to press Control-Alt-F1 to get to a terminal freezes the entire system. The only solution is to reboot.

I have a Microsoft Wheel Mouse Optical. The light stays on after it quits, but unplugging it and plugging it back in after it quits results in the light not coming on. Other USB devices work (and continue to work) fine; however, I have a USB-to-serial adapter that I use to program a number of BASIC Stamp microcontrollers that I have, that routinely gives me headaches and often refuses to work.

Furthermore, I've tried checking dmesg for errors, and have even brought up the log viewer (System -> Administration -> Log File Viewer) and used my computer until my mouse quit, but no messages appeared even after my mouse quit.

The problem has not gone away after upgrading to Ubuntu 9.10.

I have not attempted upgrading my BIOS.

My current setup is as follows:

Motherboard: ASUS M3N78 PRO
Processor: AMD Phenom 9500 (quad-core, 2.20 GHz)
RAM: 2GB (2x 1GB) Corsair DDR2 XMS2
Fan: stock; came with the processor
PSU: Ultra 250W
Hard drives: an old 30GB IDE Maxtor (master) and a 20GB Quantum Fireball (slave); I have to disconnect the slave HD to use my CD-ROM drive.

I tried installing both the 64 and 32 bit versions of Ubuntu 9.04, but to no avail -- both suffered the same problem. I have since upgraded from the 32 bit version of 9.04 to 9.10.

I have not obtained another mouse to test.

---

### Post by XCan on 2009-11-11
I believe you should pursue your last point, obtain another mouse to test. It is, however, peculiar that your system hangs upon trying to bring up the terminal.

---

### Post by aPaSv5 on 2009-11-11
My mouse quit just now, so I grabbed another USB mouse from another machine and plugged it in **without** having unplugged the other, crapped-out mouse, and it worked. The crapped-out mouse continues to do nothing, though the light is on, and the old/new mouse that I just plugged in works beautifully.

Out of curiosity, I attempted unplugging the crapped-out mouse, and now *both* mice have quit working, and both of their lights have gone out.

Very strange.

---

