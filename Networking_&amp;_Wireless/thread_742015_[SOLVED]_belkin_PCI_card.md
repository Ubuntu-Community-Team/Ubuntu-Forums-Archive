---
title: "[SOLVED] belkin PCI card"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by hellomoto on 2008-04-01
Got my driver to install however I keep getting segmentation fault after 
sudo modprobe ndiswrapper.

Is there anyway to fix this with out having to do anything difficult like compile from source.

Ndiswrapper supported cards list says this about my card:


Card: Belkin 54g Wireless Network Card F5D7000uk

    *
      Chipset: Unknown, lspci gives ‘Belkin Unknown device 700f (rev 20)’
    *
      pciid: 1799:700f
    *
      Driver: Ndiswrapper 1.45, driver from CD - blkwgdv7
    *
      Other: Ubuntu 7.10 (Gutsy), but installed under 7.04 by uninstalling supplied version using instructions on this site, and installing latest version. Didn’t work properly (crashed system) until upgrade, so suspect kernel issues. Now using 2.6.22-14


Belkin G Wireless PCI card 

Model: F5D7000uk

version: 7000uk

ndiswrapper common 1.43
ndiswrapper utils 1.9 (i368)
ndisgtk (i368)

lspci
```

00:08.0 Ethernet controller: Belkin Unknown device 700f (rev 20)

```

lspci -n
```

00:08.0 0200: 1799:700f (rev 20)

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

ndiswrapper -l
```

blkwgdv7 : driver installed
        device (1799:700F) present

```

```

sudo depmod -a
sudo modprobe ndiswrapper
segmentation fault

```


many thanks

---

### Post by dstew on 2008-04-01
The issue seems to be a problem with ndiswrapper working with your kernel. Which version of ndiswrapper is currently installed?```
ndiswrapper -v
```

---

### Post by hellomoto on 2008-04-01
ndiswrapper -v

```

utils version: 1.9
driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586 

```

---

### Post by dstew on 2008-04-01
Probably your best bet is to compile a newer ndiswrapper version from source. It doesn't seem to be too hard to do. There is a [section in this document]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-043c7a370f7f416ffe637a052bb89d39fc75e841") that shows how. That how-to is written for broadcomm drivers, but the   same steps can be used for any driver. I think they created a directory for the newly compiled ndiswrapper with the broadcom driver name, but you can name it anything you like.

---

### Post by hellomoto on 2008-04-01
I would give this ago but you have to be connected to the internet for that to  work and my desktop hence trying to get my wifi card working on it,

I am on my wireless laptop on the moment using gutsy. 

Any other way?

---

### Post by dstew on 2008-04-01
> I would give this ago but you have to be connected to the internet for that to work With a bit of help from [nonetdebs]("http://nonetdebs.homeip.net/") you can get the packages you need, then copy them to your internet-less computer and install them. You can also update the software on your system too. Maybe update first, because there might be a new kernel or ndiswrapper package. If it still doesn't work after updating, I would install the building packages and try to compile a new ndiswrapper from source.

---

