---
title: "Partition deletion problem"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Prince Valiant on 2009-12-29
Hello,

I've deleted the wrong partitions on my Acer Aspire One.  I'm posting here in the beginner's section because I'm pretty inexperienced, and I don't want to mess anything up 'cause of a misunderstanding (that's what got me in this mess in the first place).

I've been running a dual-boot with Windows XP and UNR 9.10.  I decided to reinstall Ubuntu and switch to Ubuntu 9.10, no remix involved.  In order to do so and still retain Windows (I need it for running several programs which I can't lose and Wine won't run), I used Disk Utility while booting off a Ubuntu 9.10 flash drive to remove what I thought were Linux partitions.  I'm pretty sure what I deleted was the "extended partition."  

At any rate, when I restarted after the partition deletion (stuff was getting slow and unresponsive), I could no longer get Ubuntu running.  The computer would boot off the flash drive and give me the language and booting options for Ubuntu; I choose to run it off the flash drive, and the white Ubuntu logo is displayed, but it never actually goes to the desktop or loading screen.  

After the logo is desplayed a quickly scrolling set of text: 

```
there is a bug in some application using the D-bus library.
process 2433: arguments to dbus_pending_call_set_notify() were incorrect, assertion "pending !=NULL" failed in file dbus-pending-call.c line 956.
```

This is repeated over and over.  I can barely decipher the text (it scrolls so fast), but I'm certain this is accurate.  After letting it run for about 5-7 minutes, the screen goes blank, though the computer is on, and not in standby.  The flash drive is still active.

I've never had to make an urgent request before, but I need to have my computer usable within a day or two.  Please, help.  

Thanks in advance!

-Val

---

### Post by Paqman on 2009-12-30
Was this flash drive what you installed from in the first place? Some machines do have trouble booting from USB sticks, but if you've already got the system installed using it once then it won't be that. It's possible some files on the stick have got corrupted (flash memory sticks do have a limited lifespan), if so you might want to run the integrity check from the initial menu, and/or the .iso you downloaded.

---

### Post by Prince Valiant on 2009-12-30
Paqman,

The flash drive is fine.  As you thought, I already used it to install UNR 9.10 on this computer.  For various reasons I decided to reinstall, but never made it as far as the re-installation.  

I was deleting partitions to 'clean up' the hard drive when the problem occured.  I think that I deleted something important from the boot-loader (Grub), and maybe some swap space as well.  When I try to boot from the HD, this is what I get at the boot-loader:

```
GRUB loading.
error: no such partition.
grub rescue> _
```

There is no problem with file corruption, since I never copied any since the previous installation that I'm trying to replace.

EDIT:  I found [this]("http://ubuntuforums.org/showthread.php?t=1359802") thread, but since I can't boot from a disk (no external disk drive available), it's not much help.


Thanks for your help!

-Val

---

