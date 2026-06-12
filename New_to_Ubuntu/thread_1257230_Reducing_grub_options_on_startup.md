---
title: "Reducing grub options on startup?"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by brando337 on 2009-09-03
Hello everyone.  I recently installed ubuntu 9.04.  After which I installed the Restricted-Extras package with resulted in two different sets of ubuntu boot versions, one being before the upgrade and one after. My question is there a way to remove the older version from the grub loader so its not so cluttered? Thanks.

---

### Post by drs305 on 2009-09-03
I wrote a guide specifically on this topic, then expanded it to include details about StartUp-Manager. SUM is an excellent GUI app which tweaks a wide variety of menu options, including how many kernel options to view, menu timeouts, default OS/kernel, splash image selections, etc.

Here is the link:
[HOWTO: Grub Menu Kernel Display Options ]("http://ubuntuforums.org/showthread.php?t=818177")

The short version is you can edit menu.lst (manually or via StartUp-Manager) to limit or expand the number of kernels to view, or you can remove the kernels via APT or Synaptic, which will automatically remove them from the menu.

---

### Post by ainsworth_t on 2009-09-03
The different boot options weren't added as a result of installing restricted-extras but as a result of installing a kernel update. The best way to "remove" the other boot options from your GRUB menu is to comment them out, but not completely remove them, from your GRUB menu configuration file. To edit this file, run the following command:
```
sudo nano /etc/boot/grub/menu.lst
```

**_Note_**: Before you make changes to the GRUB menu configuration file (or any configuration file for that matter), make a backup copy of it with the following command```
sudo cp /etc/boot/menu.lst /etc/boot/menu.bak
```

Next, comment out the boot options you do not want on your GRUB menu by adding # in front of the lines starting with: title, kernel, uuid, initrd. Be careful here as it is very important you do not comment out the wrong lines.

---

### Post by Penguin Guy on 2009-09-03
[Open the terminal]("http://www.psychocats.net/ubuntu/terminal"), paste below commands in, and enter your password.
```
cd /boot/grub/
sudo cp menu.lst /menu.lst~
gksu gedit menu.lst
```

Look for something like this:
```
title		**<option you want to delete>**
uuid		33954389-0a03-4822-96c4-c6e5924de048
kernel		/vmlinuz-2.6.28-11-generic root=UUID=44549c7f-d040-4322-ae8c-c48ae0713952 ro quiet splash vga=794 
initrd		/initrd.img-2.6.28-11-generic
quiet
```

And put a '#' in front of each line as so:
```
# title		**<option you want to delete>**
# uuid		33954389-0a03-4822-96c4-c6e5924de048
# kernel	/vmlinuz-2.6.28-11-generic root=UUID=44549c7f-d040-4322-ae8c-c48ae0713952 ro quiet splash vga=794 
# initrd	/initrd.img-2.6.28-11-generic
# quiet
```

---

