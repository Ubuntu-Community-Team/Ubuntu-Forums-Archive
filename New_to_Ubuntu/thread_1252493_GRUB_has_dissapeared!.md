---
title: "GRUB has dissapeared!"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by rancor37 on 2009-08-28
I recently upgraded from windows vista to windows 7 and realized that grub had been removed (or no longer referenced during my computer’s boot sequence). According to the device manager, my ubuntu partition and swap are still present.

I’m wondering if there’s a way for me to re-establish ubuntu and access grub again without having to start from scratch. 

Any help is much appreciated!

---

### Post by earthpigg on 2009-08-28
every time you install/reinstall/upgradw windows, it will rudely take over the MBR, where GRUB hangs out.

i dont recall the exact procedure, but google searching: "windows ubuntu grub restore" will likely point you in the right direction.

---

### Post by matchstich on 2009-08-28
ok i had problems with grub, found these links

[http://ubuntuforums.org/showthread.php?t=224351&highlight=defrag](http://ubuntuforums.org/showthread.php?t=224351&highlight=defrag)

[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

[http://members.iinet.net.au/~herman546/p15.html#How_to_get_GRUBs_Command_Line_to_investigate_a_computer](http://members.iinet.net.au/~herman546/p15.html#How_to_get_GRUBs_Command_Line_to_investigate_a_computer)

there are more  links in the threads. hopefully one of them will

help you .

thanks

---

### Post by stinger30au on 2009-08-28
as a rule of thumb , your better off installing windows first

it likes to think its the only o/s on the planet allowed to run in our pc's and has its mind made up it doesnt want to play nicely with anything else

so let it have its own way and install first, then once it thinks it owns the place, install ubuntu side by side and let grub sort it out

there is a handy disc to help recover the boot up and it is super grub disc

very handy

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by LewRockwell on 2009-08-29
+1,000,000,000,000,000,000,000,000

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by rancor37 on 2009-09-02
Supergrubdisk worked great! My last question is how I can get rid of the windows boot loader menu. When I select windows as the operating system to boot into, grub will then move into the windows bootloader and give me the option between Autogrub and Windows 7. How can I get rid of the secondary loader?

Thanks again!

---

### Post by zwygart on 2009-09-02
The second bootloader is the Windows bootloader, so you have to fidel with that.
I think adjusting your boot.ini at the root of your Windows partition should be enough.
I would try to only remove the entry wich is not needed. But search on the web about boot.ini and you should have what you want.

---

