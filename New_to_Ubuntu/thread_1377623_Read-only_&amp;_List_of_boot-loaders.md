---
title: "Read-only &amp; List of boot-loaders"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by username in use on 2010-01-10
Hi,

I've used Windows OS since the dawn of my computer days. Yesterday I installed Ubuntu 9.10 on a separate partition, so I could dual-boot and explore the wonders of Ubuntu 9.10.

Everything worked out fine, but my headaches started when I wanted to change the order of my boot-loaders. I did a little Googling, read a little documentation and found out that I had to edit in the following file /etc/default/grub.cfg.

According to the documentation I read if I changed the parameter > GRUB_DEFAULT=0 to > GRUB_DEFAULT=saved then the order would depend on my last choice.

Nice I thought... until I found out I don't have permissions to edit in any system files. I Googled again, but I can't find any permanent solution that gives me full CRUD permissions to all files on startup.

Also when I open the grub.cfg file I am told to run 'update-grub' afterwards, but where is this executable located?

Any help is greatly appreciated. Thanks in advance.

---

### Post by kansasnoob on 2010-01-10
From the following thread:

> grub.cfg is not meant to be edited.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Give that a good read, especially the part on /etc/default/grub:

> # GRUB_DEFAULT - Sets the default menu entry. Entries may be numeric or "saved"

    * GRUB_DEFAULT=0 - Sets the default menu entry by menu position. As Grub Legacy, the first "menuentry" in grub.cfg is 0, the second is 1, etc.
    * GRUB_DEFAULT=saved - Sets the default menu entry with whatever was selected last. If the menu is displayed during boot, the last entry selected will be highlighted. If no action is taken, this selection will be booted at the end of the timeout or if the menu is hidden.
          o grub-set-default is enabled when this value is set to saved. You can quickly change the default OS/kernel with this command.
                + The format is "sudo grub-set-default X, with X being the menuentry position (starting with 0 as the first entry) or the exact menu string. Examples: sudo grub-set-default 3 or sudo grub-set-default "Ubuntu, Linux 2.6.31-14-generic"
                + To obtain the existing menuentry choice number (starting from 0) or the menuentry "string", run "grep menuentry /boot/grub/grub.cfg"
    * GRUB_DEFAULT="xxxx" - An exact menu entry, including the quotation symbols, may also be used. In this case, location in the menu will not matter. Example: GRUB_DEFAULT="Ubuntu, Linux 2.6.31-9-generic"

    * One time boot - If you wish to boot to a specific entry for only the next boot, run grub-reboot "desired-menuentry" as root. An accurate method of getting the menuentry correct is to copy it from the /boot/grub/grub.cfg file.

    * For an example of how to enable the "saved" option with a custom menu, see the "Custom User Entries" section.


---

### Post by mk1w86 on 2010-01-10
Take a look here for Grub2 (the version of grub with Ubuntu 9.10) information: :D

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by username in use on 2010-01-10
Sorry but please address the read-only problem and how to execute "update-grub" if possible.

---

### Post by mk1w86 on 2010-01-10
To edit /etc/default/grub run:

```
sudo gedit /etc/default/grub
```

or replace gedit with whatever text editor you want to use.

To run update-grub type:

```
sudo update-grub
```

in a terminal.


sudo gives the command root privileges.

---

### Post by marshmallow1304 on 2010-01-10
> **username in use said:**
> Sorry but please address the read-only problem and how to execute "update-grub" if possible.

To give yourself temporary root priveleges in Ubuntu, use sudo for terminal-based applications and gksudo for graphical applications.  In this case, open Applications->Accessories->Terminal and issue this command:
```
gksudo gedit /etc/default/grub
```
Make your changes, save and close, then run
```
sudo update-grub
```

---

### Post by username in use on 2010-01-10
Thanks for the help :)

---

