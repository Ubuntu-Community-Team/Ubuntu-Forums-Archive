---
title: "MP-BIOS bug IO-APIC; gedit error"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by piroko on 2009-02-21
Following the instructions from another thread, I went to do the following: 

```
gedit /boot/grub/menu.lst
add 'noapic' to the line '#defoptions='
update grub

```

But, when I go to run 'gedit /boot/grub/menu.lst' I get this error:
```
(gedit:10772):Gtk-warning**:Cannot open display
```

> **Roobert said:**
> 
I have no idea why it's happening, but I had the exact same error, and here's how I fixed it:

At the grub boot screen, use your arrow keys to highlight "kernel /boot/linuz-2.6.15-25-386 root=/dev/sda3 ro quiet splash" (your exact paths and numbers might be a little dfferent). Then type 'e' to edit the boot options; you will be taken to another screen. Append 'noapic' to the end of the boot options, and hit enter. Then just type 'b' to boot. Dapper should then boot normally.

To make these changes permanent, do the following:

Code:

sudo gedit /boot/grub/menu.lst

and append 'noapic' to the line the says "#defoptions=", then

Code:

update grub

and reboot. I took this help info from another post, none of it is original, but if I find the original post where I dea this, I will link to it from here.

EDIT: Here's the original link: [http://www.ubuntuforums.org/showthre...ht=MP-BIOS+bug](http://www.ubuntuforums.org/showthre...ht=MP-BIOS+bug)

---

### Post by piroko on 2009-02-21
bumptiy bump bumpfor heeelp.

---

### Post by snova on 2009-02-21
> **piroko said:**
> Following the instructions from another thread, I went to do the following: 

```
gedit /boot/grub/menu.lst
add 'noapic' to the line '#defoptions='
update grub

```

But, when I go to run 'gedit /boot/grub/menu.lst' I get this error:
```
(gedit:10772):Gtk-warning**:Cannot open display
```

If you don't have graphics working, Gedit can't run.

Use nano, it's a terminal editor.

```
sudo nano /boot/grub/menu.lst
```

Find the line starting with '#defoptions', remove the # character, and put 'noapic' at the end. Then press Ctrl-X to exit.

---

### Post by piroko on 2009-02-21
> **snova said:**
> If you don't have graphics working, Gedit can't run.

Use nano, it's a terminal editor.

```
sudo nano /boot/grub/menu.lst
```

Find the line starting with '#defoptions', remove the # character, and put 'noapic' at the end. Then press Ctrl-X to exit.

Alright, so, added noapic to '#defopion=' list, and ti still wouldn't load my desktop, I'm not really sure what's going on with it.
Gonna checl the hardware incompatibility list for my motherboard.

---

