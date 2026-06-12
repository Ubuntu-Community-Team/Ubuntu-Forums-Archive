---
title: "Dual Boot problems"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by Tyronekay on 2011-01-09
[B][FONT="Tahoma"]Greetings
I currently run a Windows 7/Vista 64 bit dual boot system, each running on individual drives. I recently installed Ubuntu 10.4 (64 bit) on a separate external drive &, as luck would have it, Ubuntu has given me a third boot option. Unfortunately this is causing me some concern as I had intended for Ubuntu to run as a stand alone application to be accessed mainly for testing & curiosity. I find Ubuntu a superb operating system but require more time to acquaint myself with its intricacies. To this end, I would like to remove it from my boot configuration (GRUB) but have no idea how to do this. 
Any assistance/advice would be gratefully appreciated.[/FONT][/B]:confused:

---

### Post by mikewhatever on 2011-01-10
Removing Grub is fairly easy, but more importantly, you have to figure out where it is. By default, Grub is installed to the MBR of the first (usually internal) hdd, and I suspect that you might need to restore the Windows bootloader.
Get the [BootInfoScript]("http://sourceforge.net/projects/bootinfoscript/") and run it in Ubuntu, then post the output here.

---

