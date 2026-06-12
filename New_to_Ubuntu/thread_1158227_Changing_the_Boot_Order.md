---
title: "Changing the Boot Order"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by bbro300zx on 2009-05-13
Can anyone tell me how I can change the boot order so the computer goes into Windows by default instead of Ubuntu?  

I installed Ubuntu on my computer from inside Windows so it loads into Windows by default and this is good for me since I am just learning about Linux.  But on my wife's machine I installed Ubuntu outside of Windows, so Linux or Ubuntu comes up as the default OS at the top of the list.  I could probably uninstall and reinstall Ubuntu from inside Windows like I did on my computer but I am not even sure how to uninstall it.  It seems like it would be easier to change the boot up order.  

Thanks

---

### Post by Ragnar Bocephus on 2009-05-13
The absolute easiest way to do this is to install startup manager.

```
sudo apt-get install startupmanager
```

It will then appear in your System>Administration menu.  Very easy to change the boot order on the first tab under "Default Operating System".

---

### Post by Didius Falco on 2009-05-13
> **bbro300zx said:**
> Can anyone tell me how I can change the boot order so the computer goes into Windows by default instead of Ubuntu?  

I installed Ubuntu on my computer from inside Windows so it loads into Windows by default and this is good for me since I am just learning about Linux.  But on my wife's machine I installed Ubuntu outside of Windows, so Linux or Ubuntu comes up as the default OS at the top of the list.  I could probably uninstall and reinstall Ubuntu from inside Windows like I did on my computer but I am not even sure how to uninstall it.  It seems like it would be easier to change the boot up order.  

Thanks

Welcome to the Ubuntu Forums!

A quick way to set Windows to boot up first is to make a small adjustment to your menu.lst file.

Open a Terminal shell from **Applications/Accessories/Terminal** and type ```
gksudo gedit /boot/grub/menu.lst
```

Then take a look at the very beginning of the file for the section that looks like this:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0
```

What you want to do is count the number of entries until you get to the Windows entry. Scroll down until you see this:

```
## ## End Default Options ##
```

Then count the blocks of entries to the Windows one. An easy way to do it is to just count each occurrence of the word "title". If there are four blocks that start with "title" you'd change the number to 3 where it now says "default 0"

The Grub program counts a little differently than you or I - it starts counting at 0, so it sees 0,1,2,3 where you or I would see 1,2,3,4, etc.

Save the file and you are all set.

Regards,

Didius

---

### Post by Big_astur on 2009-05-13
You have to edit the file "menu.lst" inside the folder boot/grub

In the first lines there should be one like this one:

```
default		0
```

The number might be different but it's telling which line in the grub is by default highlighted.

Now to know what you have to add go to the end of the file and you see ther a list of all the options which appear in your grub something like:

```

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		b7e66c75-9a7c-49fa-8b84-e874a379de5c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b7e66c75-9a7c-49fa-8b84-e874a379de5c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		b7e66c75-9a7c-49fa-8b84-e874a379de5c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b7e66c75-9a7c-49fa-8b84-e874a379de5c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		b7e66c75-9a7c-49fa-8b84-e874a379de5c
kernel		/boot/memtest86+.bin
quiet
```
Now the first Title line is #0, the next #1 and so on. You have to search for the one with windows and count where is placed. If I'm not wrong i guess the line where it says "another operation systems" also counts as one.

You can also change the time in seconds it waits for you to select an option in this line:

```
timeout		3
```

EDIT: I'm too slow typing :D

---

