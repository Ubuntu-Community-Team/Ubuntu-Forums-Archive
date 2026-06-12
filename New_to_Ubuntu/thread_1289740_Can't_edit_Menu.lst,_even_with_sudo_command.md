---
title: "Can't edit Menu.lst, even with sudo command"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by PistolPLC on 2009-10-12
Hi -

I'd like to edit my menu.lst file to change the default boot option.  While I've edited this file with success before, I can't seem to open it in gedit so that I can save it.  When I open a new terminal window and type 

                          sudo gedit boot/grub/menu.lst

gedit opens a blank document (titled menu.lst) that is apparently located in "home/lastname/root/grub."  (Or, would be located at this location if I were to save it, thereby creating such a folder as well, apparently.)  

Anyway, I can go into filesystem/root/grub/menu.lst and see the complete file, but I obviously can't alter the file there.  Am I missing something?  Why won't the above command open the menu.lst file that I need?  

Any thoughts?  Thanks!

- PistolPLC

---

### Post by ugm6hr on 2009-10-12
> **PistolPLC said:**
>                           sudo gedit boot/grub/menu.lst

You missed the initial / and gksudo

```
gksudo gedit /boot/grub/menu.lst
```

PS: By missing that initial "/" you are telling Terminal to look in the current directory (rather than the "root" directory), which defaults to your home directory in Ubuntu.  Hence the new file created in /home

---

### Post by tuxxy on 2009-10-12
Well I dont know if you just mistyped it here but the command was missing a /

```
gksudo gedit /boot/grub/menu.lst
```If this is GRUB2 included with Karmic then its a different file now.

---

### Post by diesch on 2009-10-12
It has to be ```
sudo gedit /boot/grub/menu.lst
``` (note the "/" before "boot")

---

### Post by falconindy on 2009-10-12
You're missing a leading / on the pathname.
```
sudo gedit boot/grub/menu.lst
```
The above defines a relative path from your current location
```
gksu gedit /boot/grub/menu.lst
```
The above defines an absolute path. It also correctly uses 'gksu' instead of 'sudo' given that you're launching a graphical app.

---

### Post by oldfred on 2009-10-12
Another way to open it is using Naulitus and becoming superuser as you open it.

Use Naulitus/file browser, places, computer, find your filesystem, drill down thru /boot/grub so you can see menu.lst. 

Do not double click as it will not let you save it but right click, choose open with, in the open with window scroll to the bottom Open with other Application, at bottom where it says use other application, click on it and it will open a single line, type in gksudo gedit and it will open the file in superuser mode so you can save it. It may seem long but is easy once you right click and scroll down.

---

### Post by PistolPLC on 2009-10-12
Well, all of that worked!  

Simple enough - simple oversight of the need for that leading "/".  I'm not quite sure I understand why this whole superuser/sudo thing is required, but that's probably for another day.

Thanks for the quick help!

Pistol

---

