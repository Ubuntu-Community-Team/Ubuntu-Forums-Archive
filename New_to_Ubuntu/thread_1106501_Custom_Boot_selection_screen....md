---
title: "Custom Boot selection screen..."
date: 2009-03-25
forum: New to Ubuntu
---

### Post by killermad34 on 2009-03-25
This may, in fact, be a giant waste of my time. But it's an idea I have and I would really like to know if there is a way that it is possible.

I want to be able to turn on my PC, and instead of that boring lines of text that say Ubuntu version XXXXXX and Windows (insert your version here) on the boot selection screen, I want to be able to make my own. Maybe a windows logo, a tux penguin that you could select between, something fancy like that lol. I know this is far fetched, but hey, I figure anything is possible.

I'm sure this would have to be something advanced. Like a smaller distro that loads said program to let you choose between the two logos, and then loads the correct partition based on which on you clicked.

Possible, impossible? Ideas? Has it been done before!? Let me know, my brain is going crazy right now.

---

### Post by cariboo on 2009-03-25
I don't think you can do what you're asking, but with startupmanager you can add a background image. You can edit the tile lines in grub using:

```
gksu gedit /boot/grub/menu
```

Here is a snippet from mine:

```
## ## End Default Options ##

title		Jaunty
uuid		e44c6e62-f018-4e73-926f-b8f51860f2c9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e44c6e62-f018-4e73-926f-b8f51860f2c9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title	        Jaunty Recovery
uuid		e44c6e62-f018-4e73-926f-b8f51860f2c9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e44c6e62-f018-4e73-926f-b8f51860f2c9 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Memtest86+
uuid		e44c6e62-f018-4e73-926f-b8f51860f2c9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Intrepid
uuid 		b3e831ac-7f40-48e4-b65e-7f4700759208
configfile	/boot/grub/menu.lst
```

startupmanager is available in the repositories

Jim

---

