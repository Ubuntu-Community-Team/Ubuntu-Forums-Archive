---
title: "What to look for when adding a windows OS?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by bcondemi111 on 2008-12-15
I've installed Ubuntu on my entire disk and have partitioned it for Windows.

(some stuff just wont run in Linux)

Anyway, haven't installed windows yet because I'm not sure where to install its boot location when I get to the end of the install???

Right now Ubuntu loades as default no problems. It will be my primary OS, and windows, whenever I can't avoid it. 

When I install Windows typically, at the end of the installation, it writes to the Master Boot Record (if I remember correctly?) When installing it now as my second OS, I don't think I have an option to write its location to Grub correct? I think there is an option to write to its partion? disk 2 (or whatever its called).

Does Grub see the windows partition and automatically add it next time I boot up the machine and the OS options are there?

thank-you

BC

---

### Post by karlr42 on 2008-12-15
No, as far as I know the Windows MBR will ignore Grub and erase it, usually leaving you no way to boot into Ubuntu.

---

### Post by howefield on 2008-12-15
> **bcondemi111 said:**
> Does Grub see the windows partition and automatically add it next time I boot up the machine and the OS options are there?

No as the poster above said, windows will overwrite you grub, leaving you able to boot into Windows but not Ubuntu.

You will need to reinstall Grub, and then add your windows install to it.

Plenty of guides around, eg

[http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/](http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/)

Scroll down past the partitioning with gparted bit as you already have a partition to take windows.

---

### Post by bcondemi111 on 2008-12-15
I hate windows even more now! What should I do then? If i'm not mistaken however I can choose for windows not to install to the mbr? can anyone confirm this?

BC

---

### Post by howefield on 2008-12-15
As above, it is not the end of the world, all you need to do is reinstall grub (overwriting the windows bootloader) and then add windows to grub.

Sounds more complicated than it really is.

---

### Post by Drakkor on 2008-12-15
If possible, it's a lot easier to install windows first , then
Ubuntu,so Ubuntu will write the mbr,or grub as it's called and show boot options. Ubuntu can partition your drive to include windows.

---

### Post by donkyhotay on 2008-12-15
Linux is designed to play nicely with other OS's, windows is programmed to be a bully. As mentioned previously there are ways of forcing windows to play nice but it won't do so by default.

---

### Post by kansasnoob on 2008-12-15
It's not really complicated at all. You didn't say whether it's Vista or XP, so here's both:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Restoring GRUB is easy:

Boot up your live CD.
In the desktop, open terminal (Applications -> Accessories -> Terminal).

```
sudo grub
```

This will set it to grub mode, then:

```
find /boot/grub/stage1
```

This will locate your boot partition. If you already know the location, you can ignore this step.

```
root (hd0,0)
```

Replace the (hd0,0) by your boot partition number. If your Ubuntu is installed in the second partition, then change it to (hd0,1).

Next:

```
setup (hd0)
```

And finally:
```
quit
```

Now reboot your system.

---

### Post by markharding557 on 2008-12-15
One option to consider is running windows in vm like vitualbox,this will run anything except 3d  applications

---

### Post by bcondemi111 on 2008-12-16
Oh... I havn't heard of that? vm is Virtual machine right?

I've got my quickbooks and x10 software running only on my xp os. Everything else runs on Ubuntu.

I really don't play games anyway... Is there some info/site I can read up on for this VM? is it a full xp installation but on the VM?

thank-you

---

