---
title: "Computer won't start up after network card switch"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by nash black on 2010-06-26
I'm running an Ubuntu dual boot with windows (XP pro and Ubuntu 10). I have two network cards installed on my computer, a dedicated card and the motherboards internal one. After having trouble getting online, I switched the Ethernet cable to the dedicated card and selected it from the drop-down networking list in Ubuntu. The computer then began briefly freezing every few seconds, so I rebooted.

The computer would not start up during and after the reboot attempt. It goes to a blank screen after loading the hard drives and displays a (blinking underscore) cursor, but nothing happens.

So now I cant even get to the grub menu to boot XP, ahh! Any ideas?

Thanks
Nash

---

### Post by -humanaut- on 2010-06-26
Disable the motherboards ethernet card from the System Bios

---

### Post by nash black on 2010-06-27
The really annoying thing was that I couldn't get into setup/BIOS or the boot menu, even when I pressed Del or F11 repeatedly during the startup it would just go to the blank screen. I tried unplugging both hard drives with the Ubuntu 10.04 installation disk in the optical drive to force it to boot from there w.o the menu, but the same screen showed up. This lead me to believe that there might be some issue with the HDs... I'm still not sure, but luckily when I plugged them back into the mobo the computer booted normally... I reinstalled GRUB and the latest image, etc just in case and the computer has been booting properly since then, windows and all. I'll pull the extra network card out just in case, but all seems well for the time being.

Thanks for the reply in any case!

Nash

---

### Post by S.R on 2010-06-28
Did you F2, F10, or del to get to this bios? It would be way to easy to do that for us.

---

