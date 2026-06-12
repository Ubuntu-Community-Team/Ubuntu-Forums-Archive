---
title: "Could not find kernel image Linux Boot:"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by scope123 on 2009-10-07
I have downloaded Netbook Remix Image from ubuntu image.
im trying to install ubuntu dual boot on desktop(XP Installed First)

made USB Drive Bootable with the image using Win32 Image Writer.

Casper Folder Contains 

vmlinuz
initrd.gz

syslinux.cfg file content under syslinux folder.

include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo

when i tried to boot i end up with the error

Could not find kernel image Linux Boot:

I googled i found lot of posts on this but even i make change in config file like below but same error.

default text
prompt 5
timeout 300
gfxboot bootlogo

label debug
kernel vmlinuz
append initrd=initrd.gz noapic nomediacheck debug usb

label text
kernel vmlinuz
append initrd=initrd.gz text usb

label expert
kernel vmlinuz
append expert initrd=initrd.gz usb

label ks
kernel vmlinuz
append ks initrd=initrd.gz usb

label lowres
kernel vmlinuz
append initrd=initrd.gz lowres usb

and i copied vmlinuz and initrd.gz in root directory.

im newbie i want to migrate from XP to ubuntu OS.
Please help me?

---

### Post by nothingspecial on 2009-10-07
It might be easier to try again with [[COLOR="Magenta"]unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/")

---

### Post by scope123 on 2009-10-07
i tried with unetbootin also but it generating same syslinux.cfg file and end up with same error.

---

### Post by scope123 on 2009-10-08
Now i extracted Image and write into the cd.it worked fine.

I rebooted my computer and selected try without any change to the computer.

it worked well.

One more problem is i booterd into windows and tried the wubi installation.
installed completely.
but im getting Gnome Power Management Error.

now again i tried to install fresh(dual boot with windows).but its showing blank screen.

should i delete registry values in windows.can anyone help me?

---

