---
title: "My netbook can't boot!"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by Black_Omen on 2010-08-19
I have a new Samsung N210 and I installed UNR 10.04 via wubi, alongside win7. I know the installation said you can't put the computer on hibernation mode, so I didn't do it... just sleep mode. Anyway, the netbook's battery charge was gone while it was on sleep mode, and the next thing I know when I power the netbook on is that after the Samsung splash screen comes on, it doesn't boot. It just goes to a black scren with a dash on the upper left corner.

Now, this had happened once before, almost the same thing, except that I was using the netbook when the battery charge was gone. On that occasion I used **Super Grub2 Disk** to boot into Win7 and then restarted the machine and everything went fine. Now I tried to do the same and... well, let's just say the ONLY way for the computer to boot is using Super Grub2 Disk. Otherwise it just stays there on that black screen with the dash. I tried uninstalling UNR and it didn't work either... so...

I'm completely stumped, AND I'm a complete n00b. So... any help is appreciated!

---

### Post by MCVenom on 2010-08-20
It sounds like you need to reinstall the Windows Bootloader.

Boot into Windows 7 from the Super Grub Disk, then once you're in there, download and install [EasyBCD]("http://neosmart.net/dl.php?id=1").

Then run EasyBCD. Click the button that says 'Bootloader Setup', then click the 'Install Windows Vista/7 bootloader to the MBR' radio button. Then, click the 'Write MBR' button.

Restart, and your computer should boot to Windows 7 again. :)

---

