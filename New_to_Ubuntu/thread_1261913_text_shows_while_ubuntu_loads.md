---
title: "text shows while ubuntu loads"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by libihero on 2009-09-09
after i downloaded the kde desktop, the loader for ubuntu started to show text instead of the bar progressing.  it would first show the logo with the bar having a line go back and forth, then it goes right into the text.  i tried startup manager, but that didnt seem to help :(

---

### Post by ecmatter on 2009-09-09
```

sudo nano /boot/grub/menu.lst

```look at the first entry under "## ## End Default Options ##".  It should look something like this (note the boldface):

```

title           xubuntu 9.04, kernel 2.6.28-15-generic
uuid            325ddc57-bn0f-4861-898d-bg798e012a42
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=325ddc57-bn0f-4861-898d-bg798e012a42 **ro quiet splash**
initrd          /boot/initrd.img-2.6.28-15-generic

```

be sure that the options at the end of the 'kernel' line include 'quiet'.  That should get rid of the text during bootup.

---

### Post by libihero on 2009-09-10
it does tho
```
#title          Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid           7e1fac39-534e-4a88-b858-2b2412ff7086
#kernel         /boot/vmlinuz-2.6.27-7-generic root=UUID=7e1fac39-534e-4a88-b85$
#initrd         /boot/initrd.img-2.6.27-7-generic
#quiet

```

---

### Post by XCan on 2009-09-10
I think you're looking at a commented out kernel, notice the # in front of every line.

---

### Post by libihero on 2009-09-10
i opened the file and here's what it has
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		7e1fac39-534e-4a88-b858-2b2412ff7086
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=7e1fac39-534e-4a88-b858-2b2412ff7086 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		7e1fac39-534e-4a88-b858-2b2412ff7086
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=7e1fac39-534e-4a88-b858-2b2412ff7086 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		7e1fac39-534e-4a88-b858-2b2412ff7086
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7e1fac39-534e-4a88-b858-2b2412ff7086 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		7e1fac39-534e-4a88-b858-2b2412ff7086
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7e1fac39-534e-4a88-b858-2b2412ff7086 ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7e1fac39-534e-4a88-b858-2b2412ff7086
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

splashimage=(hd0,0)/boot/grub/splashimages/medine_moon_right_below.xpm.gz
```
wat should i change?

---

### Post by RabbitWho on 2009-09-10
Did you try going into system and then Login Window and then local.. to see the splash screen settings... that's in GNOME... I assume what you have is basically Kubuntu now, I remember changing it but not how i did it. But then maybe you're talking about a different part of the boot up process.

---

### Post by libihero on 2009-09-12
i am using gnome now, so how do i change it?
i'm talking about the loading bar under "ubuntu" doesn't show anymore, it switches to showing text

---

### Post by wojox on 2009-09-12
```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```

Make sure the number in there is:

```
7e1fac39-534e-4a88-b858-2b2412ff7086
```

If not change it to that.

Then run:

```
sudo update-initramfs -u
```

---

