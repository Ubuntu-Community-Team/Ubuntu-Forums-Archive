---
title: "OS dividers in GRUB"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Happypants on 2008-12-12
I'm about pulling my hair out for what I think should be a simple fix.  I'd like to add some dividers between my OSs in grub.  EX:

Ubuntu 8.10
Ubuntu 
---openSuse---
OpenSUSE 11
---Fedora---
Fedora 10
---Failsafe Kernels---

This seems like it should be a simple edit to menu.lst, but I'm not finding it... heh.  

Any help?

---

### Post by Nepherte on 2008-12-12
This is what I use for separator:
```
# (3) Separator for other operating systems
title Other operating systems:
root
```
Just replace the title.

---

### Post by caljohnsmith on 2008-12-12
Just put the following line in your menu.lst for OpenSUSE for example:
```
title -----------OpenSUSE------------
root

```
That will create the divider line your menu.lst like what you are looking for I think; how about giving that a shot and let me know if that would work for you.

EDIT: I see I posted 30 seconds too late, good call Nepherte. :)

---

### Post by philinux on 2008-12-12
This is what I use.

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Jaunty on sdb1
configfile   (hd1,0)/boot/grub/menu.lst

---

### Post by Happypants on 2008-12-12
Thank you all for your help.  I should have been a bit more specific as to what exactly I'm looking to get. :)

I have 2 OSs available on this comp and I'd like a bit more organization (i'm adding a third so it'll get a bit wall of texty).  It's more aesthetic than anything.  

I'd like an unhighlightable lines of text that say (in a sense): 

--Ubuntu's here--
(Then lists the kernels)
--Suse's here--
(More kernel schtuff)
--Mandriva lives here--
(etc with kernel stuff)

---

### Post by caljohnsmith on 2008-12-12
> **Happypants said:**
> 
I'd like an unhighlightable lines of text that say (in a sense): 

--Ubuntu's here--
(Then lists the kernels)
--Suse's here--
(More kernel schtuff)
--Mandriva lives here--
(etc with kernel stuff)
As far as I know there is no way to make the divider lines unselectable/unhighlightable. The best you can do I think to get a divider line is to use the title/root line method. Or if you want a "sub-menu", you can use philinux's technique.

---

### Post by philinux on 2008-12-12
If you install grub to the partitions in question as I have done grub looks a lot neater. This way each OS has it's own menu.lst that will get updated automatically.
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		85eb68a1-1aa7-4e6b-9efb-aa901f59f195
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=85eb68a1-1aa7-4e6b-9efb-aa901f59f195 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		85eb68a1-1aa7-4e6b-9efb-aa901f59f195
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=85eb68a1-1aa7-4e6b-9efb-aa901f59f195 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		85eb68a1-1aa7-4e6b-9efb-aa901f59f195
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=85eb68a1-1aa7-4e6b-9efb-aa901f59f195 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		85eb68a1-1aa7-4e6b-9efb-aa901f59f195
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=85eb68a1-1aa7-4e6b-9efb-aa901f59f195 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		85eb68a1-1aa7-4e6b-9efb-aa901f59f195
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Jaunty on sdb1
configfile   (hd1,0)/boot/grub/menu.lst 
```

---

### Post by Happypants on 2008-12-12
Here's my menu.lst.  I've gotten the header to appear above "Ubuntu" and "Memtest", unfortunately not any of the others.

```
title ----------------Ubuntu------------
root
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		d6be952a-ff2f-4d2f-864e-c747bddb275b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d6be952a-ff2f-4d2f-864e-c747bddb275b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d6be952a-ff2f-4d2f-864e-c747bddb275b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d6be952a-ff2f-4d2f-864e-c747bddb275b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title-----------------OpenSUSE---------------------------
root
title OpenSUSE 11.0 - 2.6.25.18-0.2
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.25.18-0.2-default root=/dev/disk/by-id/scsi-SATA_WDC_WD2500JS-22_WD-WCANK5506328-part7
    initrd /boot/initrd-2.6.25.18-0.2-default

title------OH SHEEEEETSS!!!---------
root

title           Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid            d6be952a-ff2f-4d2f-864e-c747bddb275b
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=d6be952a-ff2f-4d2f-864e-c747bddb275b ro  single
initrd          /boot/initrd.img-2.6.27-9-generic

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            d6be952a-ff2f-4d2f-864e-c747bddb275b
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=d6be952a-ff2f-4d2f-864e-c747bddb275b ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title Failsafe -- openSUSE 11.0 - 2.6.25.18-0.2
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.25.18-0.2-default root=root=/dev/disk/by-id/scsi-SATA_WDC_WD2500JS-22_WD-WCANK5506328-part7
    initrd /boot/initrd-2.6.25.18-0.2-default

title -------------------MemTEST---------------
root

title           Ubuntu 8.10, memtest86+
uuid            d6be952a-ff2f-4d2f-864e-c747bddb275b
kernel          /boot/memtest86+.bin
quiet

```

What did I miss?

---

### Post by caljohnsmith on 2008-12-12
> **Happypants said:**
> 
```


[COLOR="Red"]title-----------------OpenSUSE---------------------------[/COLOR]
root
title OpenSUSE 11.0 - 2.6.25.18-0.2
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.25.18-0.2-default root=/dev/disk/by-id/scsi-SATA_WDC_WD2500JS-22_WD-WCANK5506328-part7
    initrd /boot/initrd-2.6.25.18-0.2-default

[COLOR="Red"]title------OH SHEEEEETSS!!!---------[/COLOR]
root

title           Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid            d6be952a-ff2f-4d2f-864e-c747bddb275b
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=d6be952a-ff2f-4d2f-864e-c747bddb275b ro  single
initrd          /boot/initrd.img-2.6.27-9-generic

```

What did I miss?
I think the only problem is you need a space after the word "title":
```
title  -----------------OpenSUSE---------------------------
root
```
:)

---

### Post by Happypants on 2008-12-12
> **caljohnsmith said:**
> I think the only problem is you need a space after the word "title":
```
title  -----------------OpenSUSE---------------------------
root
```
:)

/facepalm

It's always something pretty simple when someone else takes a look... heh.

Thanks all!

---

