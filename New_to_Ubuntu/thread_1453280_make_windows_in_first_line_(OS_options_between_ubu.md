---
title: "make windows in first line (OS options between ubuntu and windows)"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by blizta on 2010-04-13
hi everybody.....
when i  turn on my PC, it will automaticaly choose ubuntu in 7 sec. (ubuntu is in the first line)

so, how can i make windows in the first line on OS options, so i don't have to wait and manually choose windows.

---

### Post by proxess on 2010-04-13
2 Ways of doing this (I'll generalize seeing that I'm at work, can't give you specifics):

1: Force grub to boot up Windows 7 in grub's configuration file, saying that Windows 7 is number 4 in the list, in the configuration file you indicate that the default OS is number 4, then grub-upgrade (or is it update).

2: Tell grub that when It updates, to do an OS Probe first before adding in the Linux OSs and Memtest+. That way every time your Kernel updates, Windows 7 will still be number 1 in the list (or number 0).

Secret way: Try using Ubuntu as your main operating system. Trust me, it's very fun! :D

---

### Post by WitchCraft on 2010-04-13
> **blizta said:**
> hi everybody.....
when i  turn on my PC, it will automaticaly choose ubuntu in 7 sec. (ubuntu is in the first line)

so, how can i make windows in the first line on OS options, so i don't have to wait and manually choose windows.

go to /boot/grub/menu.lst

and edit the file to point default to the entry number of your windows boot entry. You can also set down the boot choose time to 2 seconds.

---

### Post by Troll_the_Great on 2010-04-13
> **blizta said:**
> hi everybody.....
when i  turn on my PC, it will automaticaly choose ubuntu in 7 sec. (ubuntu is in the first line)

so, how can i make windows in the first line on OS options, so i don't have to wait and manually choose windows.

I think the easiest way to do this is by installing StartuUp Manager. You can install it from Synaptic, or open a terminal and type:
```
sudo apt-get install startupmanager
```
Once installed, you can find it under System - Administration - StartUp Manger.It will allow you can choose the default OS, the timeout in bootloader menu, and many other things. 
Cheers!

---

### Post by blizta on 2010-04-13
witchcraft:

thanks. but there's no menu.1st in /boot/grub directory.

---

### Post by blizta on 2010-04-13
> **Troll_the_Great said:**
> I think the easiest way to do this is by installing StartuUp Manager. You can install it from Synaptic, or open a terminal and type:
```
sudo apt-get install startupmanager
```
Once installed, you can find it under System - Administration - StartUp Manger.It will allow you can choose the default OS, the timeout in bootloader menu, and many other things. 
Cheers!
thanks....... :)

it's become piece of cake :D

---

### Post by Troll_the_Great on 2010-04-13
> **blizta said:**
> thanks....... :)

it's become piece of cake :D

Glad I could help. Now, if you do not need further assistance, mark the thread as "Solved" so others can benefit from your solution.
Cheers!

---

### Post by Mykk on 2010-04-13
I would do this by booting into windows and changing the arc paths.

Change your boot.ini - to do this you need to enable hidden folders and it should (touch wood) be on the root of your c drive.

Obviously this will open in a notepad, then its just a case of changing the order in which your operating systems appear in the list.

---

### Post by proxess on 2010-04-13
Menu.lst doesn't exist in Grub (almost) 2.

---

### Post by WitchCraft on 2010-04-13
> **proxess said:**
> Menu.lst doesn't exist in Grub (almost) 2.

Right, there it's called menu.cfg.

Oh, and I think the directory is grub2 instead of grub, but I don't know for sure, I'm on a windows computer right now.

---

### Post by proxess on 2010-04-13
Actually, the file you're meant to edit is */etc/default/grub*.

Actually, all the information we're looking for is located on the [Ubuntu Wiki Grub2]("https://wiki.ubuntu.com/Grub2") Page.

---

### Post by krige on 2010-04-18
> **Troll_the_Great said:**
> I think the easiest way to do this is by installing StartuUp Manager. You can install it from Synaptic, or open a terminal and type:
```
sudo apt-get install startupmanager
```
Once installed, you can find it under System - Administration - StartUp Manger.It will allow you can choose the default OS, the timeout in bootloader menu, and many other things. 
Cheers!

Thank you Troll_the_Great! I tried startupmanager and it worked like a charm! Much better and easier than messing around with configuration files.

Does startupmanager make sure that the chosen default boot option is maintained after kernel updates?

---

