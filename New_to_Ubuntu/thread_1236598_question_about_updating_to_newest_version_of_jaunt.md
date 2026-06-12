---
title: "question about updating to newest version of jaunty and menu.lst"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by jarongg on 2009-08-10
so currently i am traveling abroad in central america and therefore have limited internet access. today ubuntu updated to the newest version of jaunty. what i am curious about, is, during the update process it asked if i want to keep the current menu.lst or change or compare. there were a bunch of options. i chose to keep the current menu.lst because i have a dual boot setup and i didn't want to deal with the hassle of getting windows back if it changed it. 

what i want to know is, since i didn't change it, am i using the older version of jaunty or did it change the menu.lst to use the new version of whatever it downloaded.  do i now have to go in and manually change where and what it boots linux from?  i am just worried that it may have downloaded the update, but because i opted not to change the menu.lst, it's just sitting in the background somewhere on the harddrive taking up space and not getting used. thanks.
jaron

---

### Post by Hospadar on 2009-08-10
No biggie
First check your currently running kernel version
easiest way is 'uname -r' in a terminal, or look at the first entry on the boot menu or menu.lst

Now look and see what is the latest version of the kernel you have installed:
You could use apt, but I think it's easier to just 'ls /boot' and see what the biggest version number is.  For me it's 2.6.28-14

Now look at your /boot/grub/menu.lst, is the first entry the same as your latest kernel version? If so, great, if not, you can edit it, for example ```
title           Ubuntu 9.04, kernel 2.6.28-14-generic
uuid            ddc9e6d3-2862-4430-b518-148d1de105a4
kernel          /boot/vmlinuz-2.6.28-14-generic root=UUID=ddc9e6d3-2862-4430-b518-148d1de105a4 ro quiet splash
initrd          /boot/initrd.img-2.6.28-14-generic
quiet

```Change the line:
kernel          /boot/vmlinuz-2.6.28-14-generic root=UUID=ddc9e6d3-2862-4430-b518-148d1de105a4 
to
kernel          /boot/vmlinuz-<your latest version number in /boot>-generic root=UUID=ddc9e6d3-2862-4430-b518-148d1de105a4 

And also
initrd          /boot/initrd.img-2.6.28-14-generic
to
initrd          /boot/initrd.img-<your latest version number in /boot>-generic

Make sure you don't change the UUID, if you copy and paste mine in, it won't boot.  That's a unique identifier specific to a hard drive partition.  You probably also want to change the title and the recovery mode option.  

The kernel and initrd lines correspond to the kernel files in /boot.  so make sure there are actually files named exactly the same as your modified boot entries (if that's where you figured your version number, you should be correct to start with).
Double check the names, if they are wrong, you won't be able to boot.

For example in my /boot folder there are files named exactly /boot/vmlinuz-2.6.28-14-generic and          /boot/initrd.img-2.6.28-14-generic

It would also probably be a good idea to copy paste the top two boot entries (the regular and recovery mode entries) to right above or below themselves in the boot list and then modify one set, that way if you monkey things up, you can just arrow down at the grub boot prompt to what you were booting before.

If you are unsure of yourself, have a livecd on hand to touch up your menu.lst if you make a mistake.  Also be sure to save a backup copy, for example 'sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup'

---

### Post by jarongg on 2009-08-10
thanks for your help. i will attempt this later and hopefully everything will go smoothly.

---

### Post by LewRockwell on 2009-08-10
confirming Hospadar is correct and following those instructions should work well

.

---

### Post by bacchusmarsh on 2009-08-16
My question relates to the menu.lst. i am trying to add acpi=force lapic to the root (see post here: [http://ubuntuforums.org/showthread.php?t=187186&highlight=laptop+powerdown]("http://ubuntuforums.org/showthread.php?t=187186&highlight=laptop+powerdown")) to rectify a powerdown problem.
How do you save changes in the menu.lst, jaunty wont let me, even after i run: "sudo update-grub" in terminal. Any suggestions?

---

### Post by mcduck on 2009-08-16
You need to edit the menu.lst file as root.
```

sudo nano /etc/boot/grub/menu.lst
```
or
```
gksudo gedit /etc/boot/grub/menu.lst
```

Remember to add the options into default options section as well, otherwise running update-grub will remove them (so you'd loose the settings during the next kernel update).

---

### Post by freak42 on 2009-08-16
may I propose an easier method?:

make a backup of your current menu.lst file
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

then issue update-grub

```
sudo update-grub
```

it should update your menu.lst files to the newest kernel(s) and leave your your other settings allone (PROVIDED THEY ARE behind the line
### END DEBIAN AUTOMAGIC KERNELS LIST )

hth
matthias

---

### Post by bacchusmarsh on 2009-08-16
thanks so much to you both, not sure if i fixed my powerdown, but that is a problem for another post...

---

