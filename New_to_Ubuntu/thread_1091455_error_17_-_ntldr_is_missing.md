---
title: "error 17 - ntldr is missing"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by risoundz on 2009-03-09
hello 



I have 2 Windows XP and ubuntu 8.10 on a SATA HD.

i was texting protools 8 on the 2nd xp and it got frozen.
I needed to shut the computer down. when i restarted it grub was fine but windows wouldn't start even on safemode.

i started again and tried linux. all fine.
when i restarted it again the following msg came up

grub error 17 

I tried it again but unplugged my IDE slave HD because normally doesn't help

and the following msg came up

ntldr is missing.


I tried the fixmbr on xp repair but didn't do much.

i don't mind to lose ubuntu but i really need to keep the 1 xp version

any help 
pleaseeeeeeeeee

---

### Post by djsephiroth on 2009-03-09
The simple method:
Boot up that Windows XP CD and perform a "Windows Repair". Do not press "R" when first given the option to repair an installation! It's confusing, I know, but go on until you are about at the point that you can make partitions and install Windows. The installer should detect the copy of Windows already on your hard drive and prompt you to perform a "Windows Repair". The Windows system files will all be deleted and reinstalled; don't worry, your files and programs will not be affected. After the reinstall, your Windows settings may need to be changed, as they will all be reset by the reinstall.

The slightly more complicated method:
Copy the ntldr file from a working PC to a flash drive or slipstream it onto your Windows XP CD. Pop in your XP CD and boot from it. When given the option to repair your installation, press "R". You'll be taken to a DOS prompt sort of screen. Select your Windows installation (there'll only be one) and log into it. Copy over the ntldr file from your flash drive or CD to the proper location on the hard drive. Reboot and enjoy.

---

