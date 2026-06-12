---
title: "Booting to Recovery Mode"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by russki_drewski on 2009-11-01
I've just installed Karmic and its the only os on my computer. This means that I'm given no grub menu at startup.

How can I restart my computer and enter into recovery mode?


russki_drewski

---

### Post by shadow120 on 2009-11-01
when grub comes up hold down shift

---

### Post by pgar23 on 2009-11-01
or you can edit the grub.conf file to allow a specified time and amongst other options.

Before doing this, I highly recommend backing this file up, just in case you edit the wrong thing.
```

sudo cp /boot/grub/grub.conf /boot/grub/grub.conf.bak
```

Edit the grub.conf file: (There are small hints in this file that will be understandable even for a newb.)
```

sudo gedit /boot/grub/grub.conf
```

---

### Post by drs305 on 2009-11-01
Since you don't see a menu, I'm assuming this is a clean install with Grub 2 as your bootloader. 

The file you want to edit, if you want to always see the menu at boot, (if you don't use StartUp-Manager) is actually /etc/default/grub

Here is a link to 5 common tasks for Grub 2, including changing the timeout:
[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

One GUI app that can also do this is StartUp-Manager. It's included in the above link or you can click on SUM in my signature line.

For a complete overview of Grub 2, click on the GRUB2 link below or [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275").

---

### Post by russki_drewski on 2009-11-01
Thank you all. You've been more than helpful and quite prompt.

I didn't need to edit any of the configuration files.

Holding down shift was all I needed. Thx a ton.

russki_drewski

---

