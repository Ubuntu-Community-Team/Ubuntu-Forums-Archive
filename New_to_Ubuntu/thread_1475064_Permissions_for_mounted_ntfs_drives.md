---
title: "Permissions for mounted ntfs drives"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by _nikolaos on 2010-05-06
Using Gnome: I am going to the menu

Places->(My disk name) 

in order to mount some NTFS usb-drives and browse them with nautilus.

Those folders have code-700 permissions. Whenever I right-click on properties to change their permissions, it is not possible.

I am certain there must be a way to configure these (default?) permissions when mounting with gnome. Something like "dmask=777" in the /etc/fstab, but I don't want to use fstab or a terminal command.

Am I correct?

---

### Post by HarrisonNapper on 2010-05-06
Don't know about without using a terminal command. If owner is root, Alt-F2 then "gksudo nautilus" enter root password and you should have access.

---

### Post by _nikolaos on 2010-05-06
Actually my idea is to access an ntfs drive through apache, and I stuck into the same problem as stated there:

[http://ubuntuforums.org/showthread.php?t=684617](http://ubuntuforums.org/showthread.php?t=684617)

In my case, there will be usb drives changing, so I cannot configure permanently the /etc/fstab. I think there must be something more flexible...

(edit)

Installed NTFS configuration tool, and worked!

---

