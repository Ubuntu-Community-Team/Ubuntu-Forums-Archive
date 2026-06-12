---
title: "Installing Ubuntu 10.10"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by Livermoreb on 2011-02-22
I have a laptop which had PCLinuxOS installed on it and decided to try Ubuntu 10.10. I ordered a disc and tried to instal the system on the laptop. It seemed to go though all the stages but I could not open Ubuntu. I tried the disc on a Windows PC to see if there was a fault with it but this worked fine.

I therefore decided to try reinstalling Windows on my laptop using the original system recovery discs. This seemd to work OK but when I try to reboot the system all I can get is an error message which says:

GRUB Loading, please wait..... 
Error 17

I tried rebooting with the Ubuntu disc in the CD drive but this does not work either.

Does anyone know what has happened and how/if I can restore the system?

---

### Post by Mariane on 2011-02-22
I would advise you to restart from scratch. Use your window disk to reformat the whole hard disk and then install windows. After that install Ubuntu, selecting the option "installing the OS side by side". 

Check the available disk space when you reach that point, the sum of both partitions should be equal to the total of your hard disk (a few MB more or less does not matter, it's not really precise). 

In my experience Ubuntu install itself fine next to windows but has problems installing itself next to another Ubuntu version. I notice that because if I have an old version of Ubuntu the corresponding disk space does not appear at the stage where you are asked if you want to install the OS side by side. Suddenly I'm short of 100 GB or something like that, a big chunk of disk is missing. 

Mariane

---

### Post by Quackers on 2011-02-22
Welcome to UF
Unfortunately the "install alongside" option in the 10.10 installer tends to over-write previous installations, so I would not recommend that option.
Please boot from the Ubuntu Live cd/usb (changing bios settings, if necessary) and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Livermoreb on 2011-02-22
Thanks for the advice guys but I can't get beyond  trying to boot the systm. All I keep getting is 

[INDENT]GRUB Loading please wait...
Error 17

Any ideas? 

:([/INDENT]

---

### Post by Ben Page on 2011-02-22
> **Livermoreb said:**
> Thanks for the advice guys but I can't get beyond  trying to boot the systm. All I keep getting is 

[INDENT]GRUB Loading please wait...
Error 17

Any ideas? 

:([/INDENT]

Reinstall GRUB, GRUB is Ubuntu's bootloader. You can do it from the live CD. Or if you want to boot Windows, insert Windows installation DVD, and choose recovery tools. Then type *bootrec.exe/fixmbr* and *bootrec.exe/fixboot*in the command prompt.

---

