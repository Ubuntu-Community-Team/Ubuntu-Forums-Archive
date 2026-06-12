---
title: "Help with permissions"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by edcouch on 2009-04-09
Hi all!
When I try to uninstall the old version of clamav using synaptics package manager, it does the uninstall.  But, when I go into the file system and look through etc I see a clamav folder still there.  when I right click on it it won't let me send it to the trash because it says I am not the owner etc. etc.
My question is: How do I get rid of that clamav folder?? Your help is always appreciated!

---

### Post by iaculallad on 2009-04-09
How about doing the command below on your terminal:

```
sudo rm -r /etc/clamav_folder_name
```

?

---

### Post by edcouch on 2009-04-09
Thanks very much worked perfectly!

---

### Post by 3rdalbum on 2009-04-09
Your ordinary user account does not have write/modify/delete permission to anything within the operating system or system-wide programs. This is normal - it protects the system, it protects you and it protects other users of the system.

There is one user that has permission to everything - it's called "root" and it is the administrator of the machine.

You can elevate to root by putting the word "sudo" before any command you type (such as the one you just did), putting the word "gksudo" before any GUI program you run (for instance "gksudo nautilus" which opens a file browser as root) or by installing the "nautilus-gksu" package from Synaptic Package Manager, which adds a "Open as Administrator" item to your right-click menu in the file manager. You can open files or folders with the Open As Administrator menu item.

---

