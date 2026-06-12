---
title: "Help, Windows Vista mounting and grub problemwhen I want to mount my ntfs filesystem"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by ALF102 on 2010-08-25
when I want to mount my ntfs filesystem I get this message:

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


When I want to enter my windows vista, its gone from my Grub menu.

---

### Post by phillw on 2010-08-25
Hi,
assuming you are not running a RAID system, my advice would be to re-install the vista boot system. [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) 
> How to restore the Windows Vista or 7 bootloader
You need not worry, that will not touch your ubuntu area. Once the vista system is booting okay, you can follow the same thread to put grub back on > How to restore the Ubuntu grub bootloader (9.10 and beyond) It is important to get windows 'happy' first. There are several reasons as to why things went wrong, but that should get you back up and running.

Regards,

Phill

---

### Post by ALF102 on 2010-08-25
uhm, let me try to make it a bit clearer. I can't mount my C:/ drive.....and when I restart, Windows Vista is not there on the Grub menu. Running sudo update-grub2 shows there's no Windows Vista on the boot list and when I open grub.cfg, Vista isn't there too. Is there a way to really fix it. I don't think I want the Vista bootloader.

---

### Post by oldfred on 2010-08-25
From a Vista repair CD run chkdsk. You need to run it until you get no errors as it does not always fix everything in one pass.

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by ALF102 on 2010-08-25
Thank for the links, I don't have the Recovery disk so I'm gonna download and and do the chkdsk.

---

### Post by ALF102 on 2010-08-27
Works great, had to do the chkdsk twice. But still thank you soo much for the Vista recovery.iso links.

---

