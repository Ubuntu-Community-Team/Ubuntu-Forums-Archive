---
title: "Windows XP and Ubuntu boot Error"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by bobby1991 on 2009-03-13
Hello,
I recently installed Ubuntu 8.10 via Wubi on my computer that was originally using Windows Xp.
I had no problem logging in to either OS and it was working fine however about an hour ago i attempted to boot windows and it began to scan my usb memory stick for errors, it then became stuck and i was forced to hard reboot and now neither Windows Xp or Ubuntu will boot.
Ubuntu does not load fully and displays the following message:

[B][B]Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sda1 sda1 -o force

Or add the option to the relevant row in the /etc/fstab file:
               
                   /dev/sda5 /root ntfs-3g force 0 0
Could not mount the partition /dev/disk/by-uuid/44cc5ad2cc5abe3c. This could also happen if the file-system is not clean because of an operating system crash, or an interrupted boot process, or beacause of an inproper shutdown, or if a removable device was unplugged without unmounting/ejecting it first. To fix this, simply reboot into Windows, let it fully start, log in,ideally run a chkdsk /r, then gracefully shut down. Once you restart, you should be able to resume the installation. (filesystem = ntfs, error code = 15)

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu7) bult in shell (ash)
Enter 'help' for a list of built in commands.[/B][/B]

Windows will begin to load then a blue error screen flashes and the computer automatically reboots to the boot menu.

Im very new to linux and my skill with Windows XP is very limited so could you please help me
Thanks,
Robbie

---

### Post by BDNiner on 2009-03-13
What is the error on the windows blue screen that is preventing the computer from booting into windows?

---

### Post by carml on 2009-03-13
Try to use a recovery disk for Windows and boot from that,this just to correct the issues inside WinXP.

---

### Post by bobby1991 on 2009-04-10
Sorry for such a late reply
i solved the problem by backing up all my files and reinstalling ubuntu i now run win xp on virtualbox instead its a big improvement
thanks

---

