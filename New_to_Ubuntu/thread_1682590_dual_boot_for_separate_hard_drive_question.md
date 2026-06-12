---
title: "dual boot for separate hard drive question"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by smgarey on 2011-02-06
hi everyone, im brand new to linux and too dual booting also, i have xp installed on my main system and a few days ago installed ubuntu on an an older machine to try it out. my question is- i would like to take the hard drive from the linux machine and create a dual boot system on my main xp machine, is this possible and is it complicated. i dont mind re-installing ubuntu since its a fresh install anyway.

---

### Post by Paqman on 2011-02-06
Nope, that's pretty easy.

You could either simply put the drive from the old machine in the new one and [reinstall Grub]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2") so that it'll boot. Or you could just plug the drive in and reinstall Ubuntu, making sure you pick that drive as the target for the installation. The second option is probably simpler, as long as you don't pick the wrong drive and overwrite Windows!

---

### Post by YesWeCan on 2011-02-06
Right.
And I would further suggest you physically disconnect your XP drive while you are getting Ubuntu to boot. This prevents any accidents and simplifies things no end. Then, shutdown and reconnect the XP HD and tell the bios to always boot off the Ubuntu HD. Once booted into Ubuntu run 'sudo update-grub' and this will scan your XP disk and add an entry to the grub boot menu for XP. Then reboot and select XP and it should boot.

XP has been known not to cooperate (vast understatement :p) and there are further work-arounds if it won't boot. Come back here if that happens. You will always have the fail-safe of being able to tell the bios to boot the XP disk directly if necessary.

---

### Post by smgarey on 2011-02-06
yes, i hoped i could it like that but worried that i was being a bit naive :) thanks for the quick reply.

---

