---
title: "Booting problem after XP reinstall"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by briapro on 2011-02-04
I had to do a repair install on my Windows XP system and found that my Ubuntu installation would no long boot from the menu option in the boot.ini menu. My Ubuntu was installed from windows on the root (only) partition. In an attempt to fix the problem I ran the command sudo grub-install --root-directory=/mnt /dev/sda. Now when I boot I get the grub menu which was not the intent. Is there a way to restore back to the working boot.ini menu?

---

### Post by shof2k on 2011-02-04
I would repair your XP install again. This should reinstall the windows boot loader, then you can edit the boot.ini file to use Ubuntu.

Dual booting between XP and Ubuntu is better handled using Grub as XP isn't very tolerant of other operating systems.

Hope this helps.

---

### Post by drs305 on 2011-02-04
If you are on an Ubuntu LiveCD, you can install lilo, then run another command to return control to Windows:

This assumes your Windows partition is on sda and has the necessary boot flag (which should not have changed):

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Do not run any other commands requested by terminal messages. These are the only two you need. Reboot and you should see your Windows bootloader screen.

---

### Post by briapro on 2011-02-04
Thanks for the quick replies!

drs305 - The commands ran successfully but nothing changed when I rebooted. I forgot to mention that I am using the Live CD now - that is what I used to run the commands. Do I need to be logged on to my sda installation? If so would you tell me how to do it?

---

### Post by Tyggna on 2011-02-04
easiest way to do this would be to get the super grub cd.  You pretty much just pop it in and follow the prompts and it'll fix everything.

---

### Post by lisati on 2011-02-04
> **briapro said:**
> I had to do a repair install on my Windows XP system and found that my Ubuntu installation would no long boot from the menu option in the [COLOR="Red"]boot.ini[/COLOR] menu. My Ubuntu was installed from windows on the root (only) partition. In an attempt to fix the problem I ran the command sudo grub-install --root-directory=/mnt /dev/sda. Now when I boot I get the grub menu which was not the intent. Is there a way to restore back to the working boot.ini menu?

Is this a Wubi installation by any chance?

---

### Post by briapro on 2011-02-04
> **lisati said:**
> Is this a Wubi installation by any chance?

Yes, I am pretty sure.

---

### Post by briapro on 2011-02-04
> **Tyggna said:**
> easiest way to do this would be to get the super grub cd. You pretty much just pop it in and follow the prompts and it'll fix everything.
 
I used the Super Grub 2 cd and was able to get to my Windows boot loader and boot into XP but I am still unable to get into my Ubuntu installation. When I choose Ubuntu I get an message: Font format error - can't read section name. Then it reboots.

---

### Post by briapro on 2011-02-04
Update!
 
After running chkdsk and a couple reboots I am now able to log into my Ubuntu install I still have to use Super Grub 2 to get to the windows loader though because when I boot without it I go into grub. Can someone tell me how to get rid of grub now?

---

### Post by wilee-nilee on 2011-02-05
> **briapro said:**
> Update!
 
After running chkdsk and a couple reboots I am now able to log into my Ubuntu install I still have to use Super Grub 2 to get to the windows loader though because when I boot without it I go into grub. Can someone tell me how to get rid of grub now?

Post 3 has the commands to restore the MS boot, run them from the live cd with; in software sources, universe ticked on. Software sources must be enabled to be seen on the live cd, right click the menu-edit go to admin and click it on.

---

### Post by briapro on 2011-02-05
I am now posting this from my Wubi installation and marking this issue solved. I followed the directions here: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) to restore the XP bootloader. The bootloader was restored but at first I could only get into the XP installation. Ubuntu was giving the error "font format error: can't read section name.  So then I ran chkdsk /p because it has helped with boot problems in the past. After that and several boots and booting into repair mode it booted up cleanly. Thanks to all who offered help.

---

