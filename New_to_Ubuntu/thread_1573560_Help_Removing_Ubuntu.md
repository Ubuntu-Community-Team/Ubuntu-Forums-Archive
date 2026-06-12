---
title: "Help Removing Ubuntu"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by jmundinger on 2010-09-12
I have a netbook that I have set up as dual boot xp/ubuntu.  I would like to uninstall ubuntu from that computer and reformat the three partitions that it occupies for storage that is accessible from XP.  However, I am concerned that, if I simply delete and reformat those partitions, I will delete GRUB and then will not be able to boot the computer into Windows.

So, prior to doing anything else, I thought the appropriate first step would be to boot into the recovery console and do a fixmbr.  The netbook uses a usb cd/dvd drive.  I am able to boot into the setup cd.  However, when I attempted to enter the recovery console, I got an error message to the effect that my computer did not have a hard disc.  As an alternative, I "installed" the recovery console on the computer.  It now shows up as an option in the windows startup menu.  However, the computer locks up when I attempt to boot from that menu into the recovery console.

I presume that GRUB is in the first (and smallest) of the three partitions that were created when I installed Ubuntu.  If that is correct, can I leave that partion intact and delete the other two?  If so, will GRUB continue to function properly?  If I delete all three and do nothing else, will the computer default to the MBR and boot normally into XP?

Any suggestions about how to proceed would be appreciated.

---

### Post by wilee-nilee on 2010-09-12
It could be a sata problem or a XP cd that just isn't working. Your on the right track with doing the fixmbr first, try this ISO burned to a cd it should work to get the command line to run fixmbr.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

I am assuming here that it is your disc, and that your getting to the correct command terminal.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

Also grub is not in a partition it resides in the MBR. There are grub files in Ubuntu but what your trying to get at are in the MBR.

---

### Post by garvinrick4 on 2010-09-12
Put your Windows Grub back in place. When you delete the partition that has Ubuntu then you delete where grub looks for boot/grub. Put your XP boot back in place. If your sda1 is a boot partition leave it be, why goof around with it you are not going to move your windows install over. I like to have a copy of gparted burned to a CD that way you can work on your partitions or use a Ubuntu live CD (install cd) and use the gparted package. 
 Sounds like you know how to use your Windows CD and install your boot manager. If you do not have a Windows CD you can do it with Ubuntu CD with package called lilo.

---

### Post by beew on 2010-09-12
It looks like you should do the fixmbr AFTER you uninstall Ubuntu according to this guide.
[URL="http://www.ekoob.com/how-to-uninstall-ubuntu-from-dual-boot-windows-environment-safely-7439/"]
_http://www.ekoob.com/how-to-uninstall-ubuntu-from-dual-boot-windows-environment-safely-7439/_[/URL]

---

### Post by jmundinger on 2010-09-12
Thanks for your prompt response to my question

> **wilee-nilee said:**
> It could be a sata problem or a XP cd that just isn't working. Your on the right track with doing the fixmbr first, try this ISO burned to a cd it should work to get the command line to run fixmbr.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

I presume that the XP cd is ok.  It is a sp3 slipstream version that I made and have successfully used a few times to reinstall windows.  However, I built the cd from a Dell OEM windows reinstallation cd.  Perhaps that is the issue, i.e. it is not compatible with the Acer netbook.

Thanks for the link.  I will try that version.


> **wilee-nilee said:**
> II am assuming here that it is your disc, and that your getting to the correct command terminal.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

I got as far as the welcome screen when I booted from the setup cd.  I got the error message after attempting to enter the recovery console.

> **wilee-nilee said:**
> Also grub is not in a partition it resides in the MBR. There are grub files in Ubuntu but what your trying to get at are in the MBR.

I presume that means that I was correct in assuming that, if I delete and reformat the Ubuntu partions, the computer will not boot into windows.

---

### Post by beew on 2010-09-12
> I presume that means that I was correct in assuming that, if I delete  and reformat the Ubuntu partions, the computer will not boot into  windows.

It won't, that's why after you delete the Ubuntu partition, you boot from the windows cd and do fixmbr.

---

### Post by jmundinger on 2010-09-12
> **beew said:**
> It looks like you should do the fixmbr AFTER you uninstall Ubuntu according to this guide.
[URL="http://www.ekoob.com/how-to-uninstall-ubuntu-from-dual-boot-windows-environment-safely-7439/"]
_http://www.ekoob.com/how-to-uninstall-ubuntu-from-dual-boot-windows-environment-safely-7439/_[/URL]

Thanks for that link.  Even though that appears to be a Windows Vista solution, I presume the solution also works that way for xp.  If that is the case, it sounds like I had the right procedures, but in the wrong order.  Either way, I want to make sure I can access the recovery console before I actually make any changes to the computer.

---

### Post by wilee-nilee on 2010-09-12
I can switch my MBR back and forth between grub and the MS bootloader with no problems all day. This does not mean that for some freak reason this would be different on your computer.

The MBR is just 512MIb of the 1st part of the disc that can be rewritten at will.

garvinrick4 does mention lilo though this works for booting windows if needed.

---

### Post by oldfred on 2010-09-12
Instructions on reinstalling boot loaders to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by garvinrick4 on 2010-09-13
If your Windows CD is not working for some reason.
Insert Ubuntu CD choose try ubuntu and open a terminal:
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```
If it shows an error do not worry about it we just wand the mbr piece.
rick@rick-laptop:~$ aptitude show lilo
Package: lilo
State: not installed
Version: 1:22.8-8ubuntu1
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,221k
Depends: mbr, debconf (>= 1.2.9) | debconf-2.0, libc6 (>= 2.7),
         libdevmapper1.02.1 (>= 2:1.02.20)
Suggests: lilo-doc
Conflicts: manpages (< 1.29-3)
Description: LInux LOader - The Classic OS loader can load Linux and others
 This package contains lilo (the installer) and boot-record-images to install
 Linux, OS/2, DOS and generic Boot Sectors of other OSes. 
 
 You can use LILO to manage your Master Boot Record (with a simple text screen,
 text menu or colorful splash graphics) or call LILO from other Boot-Loaders to
 jump-start the Linux kernel.

---

### Post by jmundinger on 2010-09-13
> **wilee-nilee said:**
> It could be a sata problem or a XP cd that just isn't working. Your on the right track with doing the fixmbr first, try this ISO burned to a cd it should work to get the command line to run fixmbr.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

I downloaded that ISO and burned a cd - I presume correctly because it seems to function as an xp setup cd.  With that cd in place, I re-installed the recovery console to the windows startup menu.  However, when I attempt to boot into the recovery console, the computer locks up.

When I boot to the setup cd, I get the menu with the three choices - to install xp, to go to the recovery console or to exit.  If I select the recovery console or if I select the option to install xp, I get the error message that says that setup did not find any hard drives.

According to GRUB, windows is installed in /dev/sda2.

---

### Post by jmundinger on 2010-09-15
I have had an interesting, though not very helpful, email/chat exchange with Acer's technical support regarding this issue.

Apparently, there is something about the design of the Acer computers - at least the Aspire One netbook - such that, following modification of the master boot record, it might not be possible to access the recovery partion that was created at the factory.  Moreover, it might not be possible to reinstall the windows xp operating system using the recovery media purchased from Acer.

I find it curious that, even though the tech support folks who have responded to my posts have given me those responses, they continue to encourage me to either return the computer and they will re-install the operating system for me.  Alternatively, I can arrange for telephone support.  It makes no sense to do that because the netbook works just fine as a dual-boot machine.  Even though I might not be able to reinstall windows xp on that machine, I suspect that, if both operating systems failed, I would not have too much difficulty reinstalling Ubuntu.

I also suspect that there is a solution - probably fairly simple - but I would have to pay Acer to get it.

---

### Post by cgroza on 2010-09-15
Man, you do everything just to be sure you will not fail. I guess this behavior is more superior than mine cuz i just read the instructions once and jump into the unknown.

---

### Post by jmundinger on 2010-09-15
> **garvinrick4 said:**
> If your Windows CD is not working for some reason.
Insert Ubuntu CD choose try ubuntu and open a terminal:...
 You can use LILO to manage your Master Boot Record (with a simple text screen,
 text menu or colorful splash graphics) or call LILO from other Boot-Loaders to
 jump-start the Linux kernel.

Am I correct in understanding that - were I to uninstall Ubuntu and then was unable to boot into xp and also unable to boot into either the windows recovery console or into windows xp setup - I could run Ubuntu from the installation cd and run LILO to repair the MBR?

---

### Post by jmundinger on 2010-09-15
> **cgroza said:**
> Man, you do everything just to be sure you will not fail. I guess this behavior is more superior than mine cuz i just read the instructions once and jump into the unknown.

If it makes you feel better, setting my netbook was an exercise in reading the instructions once and jumping into the unknown.  And, fwiw, I have been very satisfied with the result.  That is why I am being cautious before reverting to an xp only machine.

---

