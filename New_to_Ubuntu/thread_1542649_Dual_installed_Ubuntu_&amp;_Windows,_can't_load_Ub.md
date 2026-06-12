---
title: "Dual installed Ubuntu &amp; Windows, can't load Ubuntu"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by Uqunfu on 2010-07-30
Hi all.

I'm getting into Ubuntu because I'm sick of malware and, frankly, Microsoft.

I've installed Ubuntu as per the [instructions]("http://www.ubuntu.com/desktop/get-ubuntu/download"), with the "install inside Windows" option, but I can't get Ubuntu to load and it's not in any of the Windows menus.

When I try to reinstall it says it's all there.

What am I probably doing wrong?

---

### Post by JustinR on 2010-07-30
Do you mean you used the program Wubi to install Ubuntu inside Windows?

---

### Post by Uqunfu on 2010-07-30
> **JustinR said:**
> Do you mean you used the program Wubi to install Ubuntu inside Windows?

Yes.

---

### Post by jtarin on 2010-07-30
I assume your talking about the [WUBI installation]("http://wubi-installer.org/faq.php#use")?
Wubi adds an entry to the Windows boot menu which allows you to run Linux. Ubuntu is installed within a file in the Windows file system (c:\ubuntu\disks\root.disk), this file is seen by Linux as a real hard disk.

---

### Post by JustinR on 2010-07-30
Wubi installed Ubuntu inside a file on your disk and is actually booted up when you restart your computer and select 'Ubuntu' from the boot manager. It does this so you don't have to actually commit to installing Ubuntu and messing around with hard drive partitions.

If you don't end up liking Ubuntu go to Add/Remove Programs on Windows and click on Ubuntu and uninstall it.

---

### Post by Uqunfu on 2010-07-30
> **JustinR said:**
> Wubi installed Ubuntu inside a file on your disk and is actually booted up when you restart your computer and select 'Ubuntu' from the boot manager.
Hmm.  I still only get the option of WinXP Pro.

---

### Post by JustinR on 2010-07-30
> **Uqunfu said:**
> Hmm.  I still only get the option of WinXP Pro.

Is Windows XP Professional the only installed operating system beside Ubuntu?

---

### Post by Uqunfu on 2010-07-30
> **JustinR said:**
> Is Windows XP Professional the only installed operating system beside Ubuntu?

Yes, however I'm moving to Linux-based because my Windows has been overrun by very stubborn malware that prevents me opening antivirus software.  I wonder if it blocks Ubuntu, too.

---

### Post by JustinR on 2010-07-30
> **Uqunfu said:**
> Yes, however I'm moving to Linux-based because my Windows has been overrun by very stubborn malware that prevents me opening antivirus software.  I wonder if it blocks Ubuntu, too.


Okay so after the BIOS screen appears, doesn't a menu show up on which operating system to select?

And Ubuntu malware is almost non-existent.

---

### Post by jtarin on 2010-07-30
> **Uqunfu said:**
> Yes, however I'm moving to Linux-based because my Windows has been overrun by very stubborn malware that prevents me opening antivirus software.  I wonder if it blocks Ubuntu, too.
Have you tried booting Windows in safe-mode and then running your anti-virus program?

---

### Post by Uqunfu on 2010-07-30
> **JustinR said:**
> Okay so after the BIOS screen appears, doesn't a menu show up on which operating system to select?

Yep.  The exact BIOS screen on the [Wubi page]("http://wubi-installer.org/faq.php#use") under "How do I select whether to run Windows or Ubuntu?", and the only option is WinXP.


> **jtarin said:**
> Have you tried booting Windows in safe-mode and then running your anti-virus program?
Yes, but it doesn't get everything, and the same trojans and other nasties just keep popping up again.  It's the Doctor AntiMalware virus, FWIW.

---

### Post by JustinR on 2010-07-30
> **Uqunfu said:**
> Yep.  The exact BIOS screen on the [Wubi page]("http://wubi-installer.org/faq.php#use") under "How do I select whether to run Windows or Ubuntu?", and the only option is WinXP.



Yes, but it doesn't get everything, and the same trojans and other nasties just keep popping up again.  It's the Doctor AntiMalware virus, FWIW.

What are the files that exist in the 'C:\Ubuntu' folder?

---

### Post by Uqunfu on 2010-07-30
> **JustinR said:**
> What are the files that exist in the 'C:\Ubuntu' folder?

3 folders: disks, install, winboot
2 files: Ubuntu, unistall-wubi

---

### Post by JustinR on 2010-07-30
> **Uqunfu said:**
> 3 folders: disks, install, winboot
2 files: Ubuntu, unistall-wubi

Whats in each folder?

---

### Post by jtarin on 2010-07-30
> **Uqunfu said:**
> Yep.  The exact BIOS screen on the [Wubi page]("http://wubi-installer.org/faq.php#use") under "How do I select whether to run Windows or Ubuntu?", and the only option is WinXP.



Yes, but it doesn't get everything, and the same trojans and other nasties just keep popping up again.  It's the Doctor AntiMalware virus, FWIW.
I would remove your malware and also remove Ubuntu and then re-install Ubuntu.
[How to remove Dr. AntiMalware]("http://www.ehow.com/how_6067077_remove-antimalware-doctor-virus.html")

---

### Post by Uqunfu on 2010-07-30
> **JustinR said:**
> Whats in each folder?

"Disks" has "boot" and "grub" subfolders, with either nothing or invisible files.  "Install" also has an ISO called "install".

"Install" has "boot" and "grub", plus "custom-install", which contains "hooks"\casper-premount, \early-command, \failure-command, \sh-command

Ubuntu\install\custom-install\packages is empty.

There's also Ubuntu\winboot\wubildr, \wubildr.cfg, \wubildr.mbr

Hope that's intelligible.


> **jtarin said:**
> I would remove your malware and also remove Ubuntu and then re-install Ubuntu.
[How to remove Dr. AntiMalware]("http://www.ehow.com/how_6067077_remove-antimalware-doctor-virus.html")
I've used some advised anti-spyware, but I'm completely the wrong person to go mucking about with root directories.  I don't have the expertise.

---

### Post by JustinR on 2010-07-30
> **Uqunfu said:**
> "Disks" has "boot" and "grub" subfolders, with either nothing or invisible files.  "Install" also has an ISO called "install".

"Install" has "boot" and "grub", plus "custom-install", which contains "hooks"\casper-premount, \early-command, \failure-command, \sh-command

Ubuntu\install\custom-install\packages is empty.

There's also Ubuntu\winboot\wubildr, \wubildr.cfg, \wubildr.mbr

Hope that's intelligible.



I've used some advised anti-spyware, but I'm completely the wrong person to go mucking about with root directories.  I don't have the expertise.

All of that is correct. So I'm not entirely sure what the problem is.

I'm not completely sure where it is in XP, but can you go right click the 'My Computer' icon on your desktop and click properties and go to 'Advanced' and under 'System' click 'Properties. What dialog does it bring up?

---

### Post by Uqunfu on 2010-07-30
Okay.  I'll uninstall and try again with the "demo and full installation" option.  Thanks for the help.

---

### Post by jtarin on 2010-07-30
> **Uqunfu said:**
> Okay.  I'll uninstall and try again with the "demo and full installation" option.  Thanks for the help.
I only installed WUBI once but didn't boot from the DVD. I booted Windows normally and when I got to the desktop I inserted the DVD and a dialog came up with several options WUBI install being one of them. If your dialog does not come up you can navigate to the DVD and find the WUBI executable and click on it.

---

### Post by Uqunfu on 2010-07-30
> **jtarin said:**
> I only installed WUBI once but didn't boot from the DVD. I booted Windows normally and when I got to the desktop I inserted the DVD and a dialog came up with several options WUBI install being one of them. If your dialog does not come up you can navigate to the DVD and find the WUBI executable and click on it.

I'm booting Wubi from a USB, but I assume it's the same process.

---

### Post by jtarin on 2010-07-30
[Not entirely]("http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/")....have you set your USB device to be the first boot device?

---

### Post by JustinR on 2010-07-30
> **jtarin said:**
> Not entirely....have you set your USB device to be the first boot device?

Wubi doesn't boot up natively. Its a Windows application if that's what both of you are talking about.

---

### Post by jtarin on 2010-07-30
> **JustinR said:**
> Wubi doesn't boot up natively. Its a Windows application if that's what both of you are talking about.And I was under the impression that this was a typical install until I read the statement > I'm booting Wubi from a USB, but I assume it's the same process.

---

### Post by Uqunfu on 2010-07-31
This is embarrassing, but I should own up for future reference.

I had the wireless receiver turned off to avoid the virus exporting my data and bringing new bots in, and I didn't watch the installation process to realise it was cancelling.  I've let it download now and it works.  Sorry to waste your time.

---

### Post by jtarin on 2010-07-31
Not a waste of time when you can learn something new.

---

