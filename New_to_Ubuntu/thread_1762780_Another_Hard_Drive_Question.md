---
title: "Another Hard Drive Question"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-19
I am thinking of keeping Windows7 on a 320gb drive, and installing linux on a 500gb drive.

Will I need to load Ubuntu Maverick 11.04 as the only drive in the system, then hook up the windows drive as a secondary?

How do you give the grub menu a choice of Windows7 or grub to boot to?

Plesase help

---

### Post by Lateralis on 2011-05-19
When you install Ubuntu, keep both drives attached.  That way, Grub will know you have Win 7 on another drive and will add a menu entry for that.  If the Win 7 drive is disconnected at installation, Grub will think you only have Ubuntu and will make a Grub menu accordingly.  

If you do decide to disconnect the Windows 7 drive from the computer before installing Ubuntu, then you can get a Win 7 entry by typing 

```

sudo update-grub

```

from the command line, once both drives are reattached and you've booted into Ubuntu.  

Hope that helps!

---

### Post by YesWeCan on 2011-05-19
Yes, keeping both connected saves doing the upgrade-grub step. However, you risk Grub being installed to the MBR of the Windows disk if you do not explicitly tell the Ubuntu installer to put Grub on the MBR of the Ubuntu disk (which is an annoying feature of the installer).
To be absolutely sure, just disconnect the Windows disk, install Ubuntu, then reconnect and make sure the bios is set to boot the Ubuntu disk first. Then run update-grub as described before.

---

