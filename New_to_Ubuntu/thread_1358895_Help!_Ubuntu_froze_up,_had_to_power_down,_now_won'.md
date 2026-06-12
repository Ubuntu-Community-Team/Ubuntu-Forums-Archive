---
title: "Help! Ubuntu froze up, had to power down, now won't boot"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by swarup on 2009-12-18
I've got a laptop setup with Gutsy/XP dual boot. I was working today in Gutsy, doing an install using Wine. The app has a lot of files (it's a book search program, with a book database), and the OS froze up in the middle of the install. Nothing would work except the screen's powder icon. So I clicked on it, selected to power down, and the computer shut down. Now it boots fine into XP, but when I select Ubuntu at the Grub screen, I get the first screen or two in the boot up process, and then the screen goes blank and nothing else happens.

Can someone tell me how to fix this? I can't imagine anything serious happened when the OS froze up, but yet I can't get the computer to boot. Thank you!

---

### Post by Chronon on 2009-12-19
Can you boot into recovery mode?

---

### Post by Temposs on 2009-12-19
Also note that Gutsy is now an unsupported version of Ubuntu. You may still get the help you need here, but the best thing to do may be to install a newer version of Ubuntu, like Ubuntu Hardy 8.04, or Ubuntu Karmic 9.10.

---

### Post by swarup on 2009-12-19
In the end, I got it fixed by booting up to the livecd. There, used gparted to identify the partition name of the Gutsy install. And using that, executed the "e2fsck -f /dev/YOUR_PARTITION" command in a terminal window. There must have been a lot of stuff that got screwed up by the OS freeze, because it must have taken 20 minutes to fix it all-- and must have asked 20 times whether I wanted such-and-such an item repaired. When it was done, I exited livecd, rebooted, and magic! Gutsy booted up just fine. Although after booting, the HDD kept on working and working like it was still trying to do something more. And not all the functions I needed in Gutsy were working. So I rebooted to the livecd-- two times more actually, each time running the "e2fsck -f /dev/YOUR_PARTITION" command, and each time finding more things that needed fixing. In the end, it seems everything has gotten repaired and the computer boots to Gutsy flawlessly, with the HDD quiet after the boot is complete, and with all the apps working properly.

---

### Post by Cuco3 on 2009-12-19
> **swarup said:**
> In the end, I got it fixed by booting up to the livecd. Then, used gparted to identify the partition name of the Gutsy install. And using that, executed the "e2fsck -f /dev/YOUR_PARTITION" command. There must have been a lot of stuff that got screwed up by the OS freeze, because it must have taken 20 minutes to fix it all-- and must have asked 20 times whether I wanted such-and-such an item repaired. When it was done, I exited livecd, rebooted, and magic! Gutsy booted up just fine. Although after booting, the HDD kept on working and working like it was still trying to do something more. And not all the functions I needed in Gutsy were working. So I rebooted to the livecd-- two times more actually, each time running the "e2fsck -f /dev/YOUR_PARTITION" command, and each time finding more things that needed fixing. In the end, it seems everything has gotten repaired and the computer boots to Gutsy flawlessly, with the HDD quiet after the boot is complete, and with all the apps working properly.Thanks for posting your fix. :guitar:

---

