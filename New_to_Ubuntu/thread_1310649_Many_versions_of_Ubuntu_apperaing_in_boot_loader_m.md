---
title: "Many versions of Ubuntu apperaing in boot loader menu"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by icjindal on 2009-11-02
I successfully installed ubuntu 9.04 on linux partition with windows vista.
After connecting to internet, upload manager installed many versions of ubuntu which are appearing boot loader menu.

How these new menu items can be removed.
regards

---

### Post by kansasnoob on 2009-11-02
> **icjindal said:**
> I successfully installed ubuntu 9.04 on linux partition with windows vista.
After connecting to internet, upload manager installed many versions of ubuntu which are appearing boot loader menu.

How these new menu items can be removed.
regards

Go to Applications > Accessories > Terminal and post the result from terminal of these commands:

```
cat /etc/issue
```

and:

```
grub-install -v
```

---

### Post by emigrant on 2009-11-02
> **icjindal said:**
> I successfully installed ubuntu 9.04 on linux partition with windows vista.
After connecting to internet, upload manager installed many versions of ubuntu which are appearing boot loader menu.

How these new menu items can be removed.
regards


```
sudo gedit /boot/grub/menu.lst
```and right after the line:
[COLOR=Red]## ## End Default Options ##[/COLOR]

you will find the list of versions the grub will show up during the startup.
you can comment by putting a '#' infront of what you don't want to show up during the startup. like how iv done:

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        becef1b2-d864-4764-828f-6381e90fd95d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=becef1b2-d864-4764-828f-6381e90fd95d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

#title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid        becef1b2-d864-4764-828f-6381e90fd95d
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=becef1b2-d864-4764-828f-#6381e90fd95d ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

#title        Ubuntu 9.04, memtest86+
#uuid        becef1b2-d864-4764-828f-6381e90fd95d
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

```

---

### Post by kansasnoob on 2009-11-02
> **emigrant said:**
> ```
sudo gedit /boot/grub/menu.lst
```and right after the line:
[COLOR=Red]## ## End Default Options ##[/COLOR]

you will find the list of versions the grub will show up during the startup.
you can comment by putting a '#' infront of what you don't want to show up during the startup. like how iv done:

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        becef1b2-d864-4764-828f-6381e90fd95d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=becef1b2-d864-4764-828f-6381e90fd95d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

#title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid        becef1b2-d864-4764-828f-6381e90fd95d
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=becef1b2-d864-4764-828f-#6381e90fd95d ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

#title        Ubuntu 9.04, memtest86+
#uuid        becef1b2-d864-4764-828f-6381e90fd95d
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

```

Or, if it is in fact legacy grub, you can just install startupmanager:

```
sudo apt-get install startupmanager
```

Which will then show up in System > Administration:

[ATTACH]134287[/ATTACH]

and limit the number of kernels that show up (I recommend 2).

---

### Post by houstonbofh on 2009-11-02
> **icjindal said:**
> I successfully installed ubuntu 9.04 on linux partition with windows vista.
After connecting to internet, upload manager installed many versions of ubuntu which are appearing boot loader menu.

How these new menu items can be removed.
regards
When you get a kernel update, it still keeps the old kernel. (Just in case) While it is a nice safety feature, it does collect after a while.  You can look in the /boot directory to see how many you have.  Then use synaptic to remove all of the versions older than the current one. (assuming it works)  Be careful that you do not remove them all.  Watch what gets "also removed" by synaptic, and if it does not have that kernel version in the title, stop!

---

### Post by icjindal on 2009-11-02
Thanks , problem solved by editing menu.lst
regards

---

