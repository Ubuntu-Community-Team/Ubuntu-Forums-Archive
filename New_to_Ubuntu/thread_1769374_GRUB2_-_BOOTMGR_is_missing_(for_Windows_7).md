---
title: "GRUB2 - BOOTMGR is missing (for Windows 7)"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by giddensg on 2011-05-27
I have Windows 7 installed on the "sda" drive and Ubuntu 10.10 on the "sdb" drive.  The "sdb" drive is the default boot drive (for Ubuntu).  The "sda" drive (for Windows) is the first drive listed within the boot menu that can be displayed by pressing the "F12" key when prompted during the boot-up process.

Presently, I can only select the Windows 7 OS using the aforementioned "F12" key during boot-up. I can start Ubuntu from the GRUB2 menu, but not Windows 7.   When selecting the Windows 7 OS from the Grub2 menu, I get the following error:  "BOOTMGR is missing" and then "Press CTRL-ALT-Delete to reboot".

History:  I had Windows 7 and Ubuntu 10.10 loaded as noted above.  Both OS'es could be selected through the GRUB menu.  I then had to resize the Windows 7 'System Reserved' partition" (using the "parted" command) to fix a problem with the Windows Image backup.  Windows 7 would then no longer boot.  I then ran the "fixmbr" and "fixboot" DOS commands from the Windows installation disk to get Windows to boot again. I then ran "update-grub". Subsequently, GRUB2 did not display a Windows 7 menu item.  I then removed and re-installed GRUB2 and ran the update-grub command which found and installed the Windows 7 menu item.  However, Windows 7 item selection fails as noted above.

I have attached the "boot_info_script" report as "boot_info.txt" and the latest update_grub log as "update_grub.txt".  Thank you for your help.

---

