---
title: "GRUB menu"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by leinad177 on 2010-03-12
is there any way to change the names or even remove some items from the boot list?

---

### Post by tom4everitt on 2010-03-12
Which version of ubuntu are you using?

Do you have a file /boot/grub/menu.lst or a file /boot/grub/grub.cfg ??

---

### Post by leinad177 on 2010-03-12
> **tom4everitt said:**
> Which version of ubuntu are you using?

Do you have a file /boot/grub/menu.lst or a file /boot/grub/grub.cfg ??


9.10 with grub.cfg

---

### Post by zeroseven0183 on 2010-03-12
Quoting from [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275), here's how you remove entries from your Grub2

> 
**[COLOR=Navy][SIZE=3]Removing Entries from Grub 2[/SIZE][/COLOR]  **
Entries should be removed by editing or removing files in the  /etc/grub.d folder. The [COLOR=DarkRed]*/boot/grub/grub.cfg*[/COLOR]  file is read-only and should not normally require editing.
[LIST]
[*][SIZE=3]**[COLOR=DarkRed]Automatically.[/COLOR]**[/SIZE]
[LIST]
[*]**Too  Many Kernels?** Kernels removed via Synaptic or with "apt-get remove"  will automatically update [COLOR=DarkRed]*grub.cfg*[/COLOR]  and no user action is required.
[LIST]
[*]In Synaptic, type the kernel  number in the search window at the upper right (for example -  2.6.28-11).
[*]Find the "linux-image" and "linux-headers" files for the applicable  kernel (example - linux-image-2.6.26-11 or  "linux-image-2.6.26-11-generic).
[*]Right click and select "Mark for Complete Removal" and then press  the Apply main menu button.
[*]The kernels will be removed from your system and from the Grub menu.
[*] If you are not sure of the kernel you are currently using, in a  terminal type "uname -r".
[*]Many users keep one previous kernel on the machine which previously  ran without problems.
[/LIST]
 
[*]Other Operating Systems which have been removed from the computer  will also be removed from the menu once "[COLOR=Navy]*update-grub*[/COLOR]"  is run as root.
[*] To prevent one of the */etc/init.d* files from running, remove  the "executable" bit.
[LIST]
[*] Example: If you don't want to see the  "Memtest86+" entries, run this command:
     Code:
     sudo chmod -x /etc/grub.d/20_memtest86+
[*]Run the *update-grub* command to allow the changes to be  incorporated in grub.cfg
[/LIST]
 
[/LIST]


[SIZE=3]**[COLOR=DarkRed]User-Created Entries.[/COLOR]**[/SIZE]
[LIST]
[*]To  remove a user-created menu entry, remove the applicable file from the  /etc/grub.d folder.
[*]If a custom file contains multiple entries, individual items may be  removed and others retained.
[*]Once the file has been removed or edited, run "[COLOR=Navy]*update-grub*[/COLOR]"  to update [COLOR=DarkRed]*grub.cfg*[/COLOR].
[/LIST]
 
[/LIST]
Hope that helps. For more information, visit the [Grub 2 Community Documentation]("https://help.ubuntu.com/community/Grub2")

---

### Post by tom4everitt on 2010-03-12
Here's a more tutorial like introduction to grub2:

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

It might seem a bit overkill just to change the name of some menu-items. Understanding grub (and grub2) is very useful linux knowledge however, especially when dual/triple/quadruple booting :)

---

