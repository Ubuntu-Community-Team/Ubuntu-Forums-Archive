---
title: "Grub Menu editing"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by omni504 on 2009-02-19
How many permissions do i have to set, damn. I thought i had already set file/folder permissions and pretty much gave myself all mod privilages. 
But nope, i was trying to edit the "menu.lst" file in the grub folder, and when i tried to save it it tells me i don't have the permission to do that. Do i need to download some more stuff so i can edit the file? I don't really like asking all these questions, but it seems that nothing is as simple as point and click on ubuntu.

The message goes something like this.

"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

---

### Post by taurus on 2009-02-19
Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by drs305 on 2009-02-19
menu.lst is owned by root. to edit it with a graphic text editor, use "gksudo"
```
gksudo gedit /boot/grub/menu.lst
```

You can also use an app called StartUp-Manager to safely edit grub. See the link in my signature line.

---

### Post by egalvan on 2009-02-19
> **drs305 said:**
> menu.lst is owned by root. to edit it with a graphic text editor, use "gksudo"
```
gksudo gedit /boot/grub/menu.lst
```


This is set so as to try to limit damage to sensitive system files.

> 
You can also use an app called **StartUp-Manager **to safely edit grub. See the link in my signature line.

I second StartUp-Manager, especially for beginners.
It's fairly safe, and mostly point&click.

I use both command-line and StartUp-Manager.

I even have a launcher on my desktop called "edit_grub",
since I'm forever "tinkering" with GRUB.
Ditto for fstab.

---

