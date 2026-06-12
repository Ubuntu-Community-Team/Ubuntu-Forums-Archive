---
title: "need help, getting this error"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by cper on 2010-12-03
hi, 

I tried to delete Ubuntu from my laptop but when i re-started I always get this error: [B]error: no such partition 
  grub rescue>

What should I do? i have tried everything and I have try booting from the windows xp disc but my computer doesn't even boot up from the disc it goes straight to that error after the Toshiba splash screen. And I set it to boot from the cd in the bios and still not working.

thanks
[/B]

---

### Post by jimingkui on 2010-12-03
You have to boot into a liveCD or usb to remove/restore the grub boot loader, make sure you have saved the changes in BIOS

---

### Post by azertyh on 2010-12-03
hello,
the [howto uninstall ubuntu](http://ubuntuforums.org/showthread.php?t=508927).

---

### Post by cper on 2010-12-04
> **jimingkui said:**
> You have to boot into a liveCD or usb to remove/restore the grub boot loader, make sure you have saved the changes in BIOS
ok, so how i do this and where do I download the livecd?

and the windows xp cd wasn't booting up becuase it need a livecd?

and thanks

---

### Post by cper on 2010-12-04
can someone please help me?

---

### Post by Penguin=) on 2010-12-04
Yeah, don't worry, go to the official windows XP site, and request a "live" CD, you will have to tell them your Windows XP version AND your computer's serial number to prove you started out with XP.

---

### Post by cper on 2010-12-05
> **Penguin=) said:**
> Yeah, don't worry, go to the official windows XP site, and request a "live" CD, you will have to tell them your Windows XP version AND your computer's serial number to prove you started out with XP.
ok thanks i'll try tha.

---

### Post by cper on 2010-12-05
i have tried downloading an xp iso and the ubuntu 10.10 and burn it into a disc and the laptop still goes straight to that error and doesn't want to load the cd im desperate.

Any other help, can you all help your are all very smart.

---

### Post by tad1073 on 2010-12-05
do you have the xp disk that cam with the laptop? If so, the link below instructs you how to reinstall windows mbr.

[http://www.chrisburgess.com.au/reinstalling-or-repairing-the-windows-xp-bootloader/](http://www.chrisburgess.com.au/reinstalling-or-repairing-the-windows-xp-bootloader/)

---

### Post by ashu. on 2010-12-05
go to bios n try totally disabling all booting device other than cd-dvd n try rebooting with the ubuntu live diskor xp disk within the cd tray....
i think ur problem arised due to jus deleting ubuntu without properly un installing the grub so the booting devise is still searching for grub files which are not present...try  the above suggestion n reply back....

---

### Post by cper on 2010-12-05
> **tad1073 said:**
> do you have the xp disk that cam with the laptop? If so, the link below instructs you how to reinstall windows mbr.

[http://www.chrisburgess.com.au/reinstalling-or-repairing-the-windows-xp-bootloader/](http://www.chrisburgess.com.au/reinstalling-or-repairing-the-windows-xp-bootloader/)
no, but I downloaded an iso windows xp from the internet and burned it; no illegal because I was just going to use to to repair and get the mbr back. I also did the same thing for ubuntu from [here.]("http://www.ubuntu.com/desktop/get-ubuntu/download")

but my laptop goes straight that error even thought i have set it up from the bios to load from a cd. Do you think its because i need the xp disk that came with the computer that it doesn't want to load nothing from those cd that i have burned?

---

### Post by cper on 2010-12-05
any one 

im really desperate:(

---

### Post by ntrgc89 on 2010-12-05
Is there an option, when you boot up, to load boot devices list? That way you should be able to tell it to boot the CD regardless. On a lot of computers its F12 (hit this repeatedly at your Toshiba splash screen until the list comes up)

Booting the XP CD and fixing from the recovery console is probably your best bet, speaking from experience.

---

### Post by fslezak on 2010-12-05
Right now the best idea is to just format the drive, and then install Windows(R)(C) to the clean drive.

Grab a copy of Hirens Boot CD, and use the Format Tools and WIPE the drive.
IF someone has knowledge of the Hirens menu, please post because I can not remember the list.

If this doesn't work, GRUB is on ROM and you have a SERIOUS Problem.

---

### Post by cper on 2010-12-06
> **ntrgc89 said:**
> Is there an option, when you boot up, to load boot devices list? That way you should be able to tell it to boot the CD regardless. On a lot of computers its F12 (hit this repeatedly at your Toshiba splash screen until the list comes up)

Booting the XP CD and fixing from the recovery console is probably your best bet, speaking from experience.yeah im trying to do that, bu the laptop doesn't want to boot from the cd. I go to the list of where it has the option to load from and when I select the cd option it still goes to that error.

---

### Post by cper on 2010-12-06
> **fslezak said:**
> Right now the best idea is to just format the drive, and then install Windows(R)(C) to the clean drive.

Grab a copy of Hirens Boot CD, and use the Format Tools and WIPE the drive.
IF someone has knowledge of the Hirens menu, please post because I can not remember the list.

If this doesn't work, GRUB is on ROM and you have a SERIOUS Problem.
ok i'll try that

---

### Post by ntrgc89 on 2010-12-06
> **cper said:**
> yeah im trying to do that, bu the laptop doesn't want to boot from the cd. I go to the list of where it has the option to load from and when I select the cd option it still goes to that error.

Hmmm... the CD might not be bootable. See if it will work on other computers, and if it doesn't, try burning a new CD but when you do, look for an option labelled "make CD bootable" or something along those lines. You can take fslezak's advice and reformat the drive if you want (or if you already have... haha), but you really don't have to. It's a simple question of fixing the bootloader.

---

### Post by fslezak on 2010-12-09
You might need to re-install Ubuntu.

After the new GRUB is back, try to install Windows and wipe the drive from the installer.

---

