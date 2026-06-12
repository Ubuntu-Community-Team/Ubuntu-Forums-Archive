---
title: "software installation"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by k-boy on 2010-08-08
I need to install a software (that comes for wireless modem) which has extension .exe when i close the tray-it ask to run the software, when i hit the Run, Archive Manager window opens after some delay the following error appears...
***error:***
[I][B][/media/cdrom0/U100_USB_Modem_Installer.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/U100_USB_Modem_Installer.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/U100_USB_Modem_Installer.exe or
          /media/cdrom0/U100_USB_Modem_Installer.exe.zip, and cannot find /media/cdrom0/U100_USB_Modem_Installer.exe.ZIP, period.[/B][/I]
can i install it using terminal???

---

### Post by dwbsr on 2010-08-08
> **k-boy said:**
> I need to install a software (that comes for wireless modem) which has extension .exe when i close the tray-it ask to run the software, when i hit the Run, Archive Manager window opens after some delay the following error appears...
***error:***
[I][B][/media/cdrom0/U100_USB_Modem_Installer.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/U100_USB_Modem_Installer.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/U100_USB_Modem_Installer.exe or
          /media/cdrom0/U100_USB_Modem_Installer.exe.zip, and cannot find /media/cdrom0/U100_USB_Modem_Installer.exe.ZIP, period.[/B][/I]
can i install it using terminal???


You can't install .exe's on Ubuntu or on Linux for that matter.

---

### Post by khelben1979 on 2010-08-08
> **dwbsr said:**
> You can't install .exe's on Ubuntu or on Linux for that matter.

Well, not entirely true but I understand your point. Using Wine software he/she actually can install MS Windows software in Ubuntu, but in this case this isn't software he/she wants to install either way.

This specific software cannot be used with Ubuntu.

---

### Post by dwbsr on 2010-08-08
> **khelben1979 said:**
> Well, not entirely true but I understand your point. Using Wine software he/she actually can install MS Windows software in Ubuntu, but in this case this isn't software he/she wants to install either way.

This specific software cannot be used with Ubuntu.

Your correct, maybe I should of mentioned Wine but his code looked like he was trying to install and .exe directly to Ubuntu :)

---

### Post by Emmtor on 2010-08-08
Is it necessary to install this software for the modem to work? In most cases, modems connected to ubuntu computers work completely fine, out of the box.

---

### Post by bodhi.zazen on 2010-08-08
> **k-boy said:**
> I need to install a software (that comes for wireless modem) which has extension .exe when i close the tray-it ask to run the software, when i hit the Run, Archive Manager window opens after some delay the following error appears...
***error:***
[I][B][/media/cdrom0/U100_USB_Modem_Installer.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/U100_USB_Modem_Installer.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/U100_USB_Modem_Installer.exe or
          /media/cdrom0/U100_USB_Modem_Installer.exe.zip, and cannot find /media/cdrom0/U100_USB_Modem_Installer.exe.ZIP, period.[/B][/I]
can i install it using terminal???

You will need to google search your exact make/model wireless modem and install the Linux drivers. This can vary from downloading the drier from the manufacturer to compiling a custom kernel to no linux driver all all.

Running the .exe, in wine or otherwise, will not work,

Sometime hardware support varies across distors, you may or may not have better luck with Fedora or an alternate distro.

---

### Post by k-boy on 2010-08-08
> **Emmtor said:**
> Is it necessary to install this software for the modem to work? In most cases, modems connected to ubuntu computers work completely fine, out of the box.
[QUOTE=k-boy]at first I connected the modem but it didn't work:(

---

### Post by bodhi.zazen on 2010-08-08
[QUOTE=k-boy]at first I connected the modem but it didn't work:([/QUOTE]

Is it working now ? If so would you post the solution of the benefit of others.

If not, simply stating that is it not working is insufficient information. We need to know the make and model of the modem and what you have tried to solve the problem.

---

### Post by k-boy on 2010-08-21
> **bodhi.zazen said:**
> Is it working now ? If so would you post the solution of the benefit of others.

If not, simply stating that is it not working is insufficient information. We need to know the make and model of the modem and what you have tried to solve the problem.

[QUOTE=k-boy]No,its not working & i didn't find any Linux software for that moreover that was my cousin's modem which i don't have now...

---

### Post by bodhi.zazen on 2010-08-21
Too bad, hardware issues such as what you experienced are frustrating.

Better luck next time.

If you require further assistance, it is always good to start by identifying the hardware by brand and model.

---

