---
title: "Dual boot problem in selecting (changing) default OS"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by Howard-BJ on 2011-08-24
As a comparative novice with ubuntu, I need help with dual boot default OS selection. I am using 11.04, a new installation on this computer (no previous installations), alongside windows XP. I want to select XP as the default OS. I have tried altering the options in start-up manager, but this does not alter the behaviour on start-up - the Grub (version 1.99) still selects and then loads (unless manually overridden) Ubuntu 11.04.

I have tried using the gedit menu.lst method, but the menu list is empty. I have another installation of 11.04 on another computer (an upgrade of many previous versions) on which I was able to edit the menu list with no trouble (selecting title 16, as that is the windows line on the menu) so I am a little confused as to why one or other of these options for altering the start-up is not working.

This is my first ever post, so I hope I have approached this the right way.

Any help / guidance gratefully received. Many thanks

Howard-BJ

---

### Post by Hreinsi on 2011-08-24
you can try this fix my install after installing win7

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

---

### Post by Hreinsi on 2011-08-24
> **Hreinsi said:**
> you can try this fix my install after installing win7

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

Sorry forgot you can start from live cd and install in terminal

---

### Post by grahammechanical on 2011-08-24
I recommend that you do what I have done and install Grub Customizer. It is in the Ubuntu Software Centre. It is a very fine utility. You can use it to set the default boot option, change the order of menu items, edit what is written on each menu line as well as setting a background image.

By the way Grub 1.99 is in effect Grub 2. It does not use menu.lst. That was for the original Grub. Here are two links.

[http://ubuntuforums.org/showthread.php?p=10340183]("http://ubuntuforums.org/showthread.php?p=10340183")

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

Someone has worked very hard on our behalf. 

Regards.

---

### Post by Hreinsi on 2011-08-24
And maybe after fixing the bootloader you can make changes in startup manager

---

### Post by ksprasad on 2011-08-24
Hi,
 
/etc/default/grub is the file you need to alter. there is a parameter called 'GRUB_DEFAULT'. Give appropriate number(starts from 0).
 
Dont forget to run 'sudo update-grub'
 
Thanks
ksprasad

---

### Post by Mark Phelps on 2011-08-24
+1 for Grub Customizer.  With the release of recent GRUB versions, especially v1.99RC, StartupManager doesn't work right anymore.  SO, I would avoid using it.

---

### Post by Howard-BJ on 2011-08-24
> **grahammechanical said:**
> I recommend that you do what I have done and install Grub Customizer. It is in the Ubuntu Software Centre. It is a very fine utility. You can use it to set the default boot option, change the order of menu items, edit what is written on each menu line as well as setting a background image.

By the way Grub 1.99 is in effect Grub 2. It does not use menu.lst. That was for the original Grub. Here are two links.

[http://ubuntuforums.org/showthread.php?p=10340183]("http://ubuntuforums.org/showthread.php?p=10340183")

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

Someone has worked very hard on our behalf. 

Regards.
Dear Grahammechanical
The Grub customiser worked fine. I forgot to save the change in preferences at the first attempt, but having overcome that minor error, it worked fine.

Many thanks for such an astonishingly rapid series of replies from so many helpful people. Hugely impressed

Howard-BJ

---

