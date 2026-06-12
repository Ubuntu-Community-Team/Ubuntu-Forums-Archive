---
title: "[SOLVED] How to modify boot loader menu?"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by kajman on 2009-01-09
Every time after I install a kernel update I get a new entry in the boot loader menu with the kernel version number. I never use the older entries so they are basically useless to me, but the menu became very large and a little bit uncomfortable to use.
How can I change this menu so it will show just one (the newest) entry?

---

### Post by nhasian on 2009-01-09
open the synaptic package manager in System-Administration->Synaptic Package Manager

click the search button, select the name field and enter linux-image.

now you can uncheck the linux kernels you dont want.  be careful not to remove the newest one or your pc wont boot afterwards.

---

### Post by kajman on 2009-01-09
This way I will uninstall those unneeded kernels, right? I think that it should do it, but I'm also curious: how to modify the boot menu directly?

---

### Post by hyper_ch on 2009-01-09
edit /boot/grub/menu.lst

---

### Post by talsemgeest on 2009-01-09
> **hyper_ch said:**
> edit /boot/grub/menu.lst
There is an option in the menu.lst that lets you change how many kernels are kept in the menu.

Also, to edit the menu.lst you will have to run this command: ```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Tomatz on 2009-01-09
Open a terminal and type:


```
sudo apt-get install startupmanager
```



Now you will have a nice GUI to configure grub with. You can also mess with colours and add an image.

---

### Post by dadozgb on 2009-01-09
> **kajman said:**
> This way I will uninstall those unneeded kernels, right? I think that it should do it, but I'm also curious: how to modify the boot menu directly?
As you edit grub config file run update-grub. Leave two kernels images just in case if something went wrong on the one you are runing.

---

### Post by supererki on 2009-01-09
sudo nano /boot/grub/menu.lst

uncomment the lines you don't like.

---

### Post by kajman on 2009-01-09
Thank you all for this helpful info :) really nice community here!

---

### Post by talsemgeest on 2009-01-09
Always happy to help! :)

---

