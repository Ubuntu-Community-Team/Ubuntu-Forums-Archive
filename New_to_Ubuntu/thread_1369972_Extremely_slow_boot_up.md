---
title: "Extremely slow boot up"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by capinredbeard on 2010-01-01
I have just installed Ubunut 9.10 on an old computer that I have (P4 - 2.4 GHz).  The computer has an ATI All-in-Wonder 7500 AGP card which I have connected to my TV through a DVI -> HDMI cable.

The problem is that the computer boots extremely slowly.  I have read about 30 second boot times; this is not that.  The boot time is more like about 5 min.  I have also read about problems with the splash screen with 7.10.  Users found that removing splash from the grub menu command would fix the problem.  Another solution (perhaps more to fixing the cause than treating the symptom) is to add a VGA*** command where the *** are replaced with a 3-digit code describing the resolution and color depth.

[https://answers.launchpad.net/ubuntu/+question/17235](https://answers.launchpad.net/ubuntu/+question/17235)
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

I have temporarily changed the grub command at bootup by hitting Esc during the loading of grub and editing the command there.  This makes the bootup much faster.  However, this is a temporary fix as the change to the menu is not permanent.

I would edit the menu.lst file, but grub2 doesn't use this file.  Can someone tell me how to edit the files in the /etc/grub.d/ folder to perform this fix?  Or point me to some other fix?

Thanks!

---

### Post by Buuntu on 2010-01-01
Grub2 basics and editing:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by capinredbeard on 2010-01-01
Other oddities (perhaps related, perhaps not):
1) My desktop background is black despite whatever I set it to.
2) Whenever I maximize a window or stretch to cover more than half the screen, it turns black.  (Firefox, File Browser, and OpenOffice Writer)

---

### Post by Buuntu on 2010-01-02
Weird... perhaps it will be fixed by installing the proprietary drivers for your video card (if any)?

First update your system by running "sudo apt-get update" in a Terminal.

Now check if there are drivers for your card in System > Administration > Hardware Drivers, install them (use the "recommended" driver if it gives you many options), and restart.  See if that fixes it.

---

### Post by capinredbeard on 2010-01-02
It says "No proprietary drivers are in use on the system."

I read somewhere about GATOS (gatos.sourceforge.net) drivers, but have yet to try them.

---

