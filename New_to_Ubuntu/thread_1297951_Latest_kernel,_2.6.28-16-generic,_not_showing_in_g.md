---
title: "Latest kernel, 2.6.28-16-generic, not showing in grub"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by donsy on 2009-10-22
Update manager just updated to the latest kernel. Option to leave menu.lst as current version chosen (because "help" said it was changed locally and I assumed that meant it was updated to show the latest kernel). But upon reboot the new kernel version wasn't there? How do I get it to show up?

---

### Post by LewRockwell on 2009-10-22
you can check for the kernel specifics by looking in your /boot directory

then you should make a backup copy of your /boot/grub/menu.lst```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```then you'll need to start a sudo session of gedit to make changes to your /boot/grub/menu.lst```
gksudo gedit /boot/grub/menu.lst
```When kernel updates require an update of the grub menu.lst file the update asks you what you want to do

You can then open a terminal session, backup the current menu.lst file(as above), and then feel secure in allowing the update session to update the grub menu.lst file since you have a backup

Then, if you need to make changes you can open two editing sessions and cut, paste, and save to your heart's content!

Honestly, once you figure out how to make backups and to compare files and to move, copy, and edit files...then *nix distros become MUCH more entertaining AND useful!

.

---

### Post by donsy on 2009-10-22
> **LewRockwell said:**
> you can check for the kernel specifics by looking in your /boot directory

then you should make a backup copy of your /boot/grub/menu.lst```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```then you'll need to start a sudo session of gedit to make changes to your /boot/grub/menu.lst```
gksudo gedit /boot/grub/menu.lst
```.


????????????????

---

### Post by alan2308 on 2009-10-22
I'll elaborate a little bit more.  At the bottom of /boot/grub/menu.lst you'll see all the kernels listed on the grub menu.  You can copy one of the entries (group of 4-5 lines), paste it where you want the new entry, and edit the title and kernel lines to reflect the name of the new kernel.  Also pay attention the line at the top of the file beginning with default.  This line specifies which kernel grub boots by default. You may need to change this as well, and it counts starting with 0

---

### Post by alan2308 on 2009-10-22
> **donsy said:**
> ????????????????

Click applications ---> accessories ---> terminal and enter those lines when the terminal opens.

---

### Post by falconindy on 2009-10-22
You need to add the entry manually. The above poster's directions will get you started. The one thing he didn't mention is... MAKE A BACKUP!
```
sudo -i
cd /boot/grub
cp menu.lst menu.lst.backup
gksu gedit menu.lst
```

After opening menu.lst, scroll down towards the bottom and you'll see a bunch of entries. Look for the one that resembles your previous kernel. It should look something like this:
```
title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		4ceb60b7-9c0a-425a-9ef5-3526713f53df
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=4ceb60b7-9c0a-425a-9ef5-3526713f53df ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.28-15-generic
quiet
```
Your UUIDs (long alphanumeric string identifying a hard drive) will be different though. You'll need to make a new entry that looks very similar. Copy the whole section and paste it into the file where you want the entry shown in the menu (probably the top). In that new entry (and only that new entry) change each instance of 2.6.28-15-generic to 2.6.28-16-generic. When you're finished, it should look like this:
```
title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		4ceb60b7-9c0a-425a-9ef5-3526713f53df
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=4ceb60b7-9c0a-425a-9ef5-3526713f53df ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.28-16-generic
quiet
```
Make sense?

---

### Post by LewRockwell on 2009-10-22
> **donsy said:**
> ????????????????

step away from the keyboard slowly now, and no one gets hurt...

.

---

### Post by tarps87 on 2009-10-22
> **LewRockwell said:**
> you can check for the kernel specifics by looking in your /boot directory

then you should make a backup copy of your /boot/grub/menu.lst```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```then you'll need to start a sudo session of gedit to make changes to your /boot/grub/menu.lst```
gksudo gedit /boot/grub/menu.lst
```

.

> **donsy said:**
> ????????????????

```
ls /boot
```
This list will contain all the kernels installed now edit the menu.lst file as posted above. Copy on of the privious sections which looks something like:
title Ubuntu, **kernel 2.6.17-10-generic**
root (hd0,4)
kernel /boot/**vmlinuz-2.6.17-10-generic** root=/dev/sda5 ro quiet splash
initrd /boot/**initrd.img-2.6.17-10-generic**
quiet
savedefault
boot

The bits in bold will be related to the kernel version, replace them with the biggest number.

If the option comes up again, select drop into shell now backup
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
Then select use package maintainers version, this way if something goes wrong you can compare the two files

---

### Post by LewRockwell on 2009-10-22
thy assistance cup runneth over

*nix distros!

ftw

.

---

### Post by donsy on 2009-10-22
Thanks to all for your help. My frustration is that ls -l shows that update manager did indeed change menu.lst at the time of the update. But it failed to add the new entry as I thought it would.

---

### Post by steveneddy on 2009-10-22
Just copy the two top entries in your menu.lst file and change the reference to kernel:

2.6.28-**15**

to

2.6.28-**16**

in the three lines of the listing.

```
gksudo /boot/grub/menu.lst
```will open the file as Administrator. You will have to input your password in the terminal.

Scroll down to the bottom, copy the last two kernel entries, then paste them over, or on top of the currect kernel entries. (see pic)

Then just change the kernel reference as described at the first of this post.

Of course do the same in the Recovery Mode section also.

---

### Post by ajgreeny on 2009-10-22
I got caught out with one of the earlier kernel updates in exactly the way the OP mentions, but luckily I knew how to put it right.

It would be more helpful, however, if the "option dialog" that appears told you that if you choose to keep your current menu.lst, the new kernel will not show and will not become the default boot kernel.  It should also therefore say that if you accept the package's default menu, you will get the new kernel at next boot as everyone would expect, I think.

Does anyone know which changes to menu.lst can be made without being noted by the system.  I assume you can change the default time, and things like a grub splash, as long as it's called splash.xpm.gz.  Call it anything else and splash will not show at the next kernel update.

This is all perhaps quickly becoming a bit anachronistic with grub2 coming in a few days, but I'm just interested.

---

### Post by LewRockwell on 2009-10-22
> **ajgreeny said:**
> I got caught out with one of the earlier kernel updates in exactly the way the OP mentions, but luckily I knew how to put it right.

It would be more helpful, however, if the "option dialog" that appears told you that if you choose to keep your current menu.lst, the new kernel will not show and will not become the default boot kernel.  It should also therefore say that if you accept the package's default menu, you will get the new kernel at next boot as everyone would expect, I think.

Does anyone know which changes to menu.lst can be made without being noted by the system.  I assume you can change the default time, and things like a grub splash, as long as it's called splash.xpm.gz.  Call it anything else and splash will not show at the next kernel update.

This is all perhaps quickly becoming a bit anachronistic with grub2 coming in a few days, but I'm just interested.

Actually, it is indeed quite relevent and will continue to be...as many folks are just now beginning their journey with Ubuntu 9.04...

.

---

### Post by ajgreeny on 2009-10-22
> **LewRockwell said:**
> Actually, it is indeed quite relevent and will continue to be...as many folks are just now beginning their journey with Ubuntu 9.04...

.
Mind you, the more I think about it, the more I realise that most people will not have ever manually changed their menu.lst file, so will never see that option box.  It doesn't stop me being inquisitive, however, about which changes are "allowed" without this option box appearing.

---

