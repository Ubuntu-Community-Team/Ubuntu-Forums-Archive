---
title: "Help! I'm stuck on Rescrue Grub!"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by Riverbum86 on 2010-10-26
Hey, I don't know if anyone is able to help me. I was trying to install  ubuntu 10.04 over ubuntu 9.10, but i had a power failure while the  installation was happening and it seems to have seriously screwed my  GRUB, because I just get stuck on a Rescue Grub command prompt. I opened  a Live Cd off a flash USB drive, and I have been trying to reinstall  GRUB using the terminal, but I can't even manage to mount my sda3  partition.

Now I am a newby at this, but i've tried all combos  that i could find to mount it. The most common command line seems to be:
sudo  mount /dev/sda3 /mnt/ (or /mnt/boot/)

But that doesn't work, it  only says I have to ''specify a filesystem type''. Nothing seems to  work. Any have a clue what I should do next?

I have a dual boot  with vista. If I could at least find my way around GRUB to boot with  windows, I could erase the whole Ubuntu partition and start the  installation all over again. I really don't feel like loosing all my  files.

Thanks for your help.

---

### Post by drs305 on 2010-10-26
Can you boot the LiveCD?

If so you can probably restore your Windows boot by installing *lilo* and have it rewrite the MBR.

But first, if you want to try booting from the Grub rescue prompt, here is a thread to help:
```

```[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

If you just want to try to write to the MBR to restore Windows, (if no Windows files are missing, just the MBR needs repair) run these commands from the Ubuntu CD. Disregard the lilo messages about not being completely installed:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
This should get Windows booting again.

If you are still having problems, run the boot info script from here and post the contents of RESULTS.txt
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

