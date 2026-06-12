---
title: "I installed virtualbox but there is no menu item in the Gnome menu?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by legolas_w on 2009-01-20
Hi
I installed and removed virtualbox several time, now I download virtualbox-2.1_2.1.0-41146_Ubuntu_intrepid_i386.deb  and tried to install it using 

```


sudo dpkg -i virtualbox-2.1_2.1.0-41146_Ubuntu_intrepid_i386.deb 

```

It take a few minutes to finish without any menu item in the Gnome menu system.

Do you know what should I do about it?

Thanks

---

### Post by Tim Sharitt on 2009-01-20
The deb for the proprietary version doesn't add the shortcut in applications for some reason, so you will need to add it manually.

Right-click on the applications menu and select 'Edit menus.' Select the sub-menu you would like it to appear under and click 'New Item'. The command to launch it is VirtualBox (notice the capitalization, it's important).

---

