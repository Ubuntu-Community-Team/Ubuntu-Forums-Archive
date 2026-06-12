---
title: "Finding Storage Media"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by padrejeff on 2010-01-02
I'm using Ubuntu on my Dell Mini.

I have a 16GB SD card in the SD slot.

How do I view all drives (especially the SD) to see what amount of space remains, etc.??

I've been away from the Ubuntu for a bit and completely forgotten how to do this :confused:

Thanks,

Jeff

---

### Post by starcraft.man on 2010-01-02
On GNOME, Places Menu > Computer usually lists all drives removable and not. Simply mount it and look inside. If your wanting to partition it up or see low level details ya can use the graphical gparted tool. 

Applications > Accessories > Disk Space Analyzer is a good tool for graphically seeing space allocation on different parts of system.

---

### Post by yeats on 2010-01-02
If you don't mind the Terminal, the easiest way to discover remaining disk space this is:

```
df -h
```

To view all mount points:

```
mount
```

---

### Post by padrejeff on 2010-01-02
> **starcraft.man said:**
> On GNOME, Places Menu > Computer usually lists all drives removable and not. Simply mount it and look inside. If your wanting to partition it up or see low level details ya can use the graphical gparted tool. 

Applications > Accessories > Disk Space Analyzer is a good tool for graphically seeing space allocation on different parts of system.

I don't know if I have Gnome or not. But, when I click Places>Computer, all that gets listed is:

Filesystem

No SD card shown there.

??

---

### Post by drs305 on 2010-01-02
In Karmic you also have System > Administration > Disk Utility, which provide information and the ability to do some basic tasks like set labels.

---

### Post by padrejeff on 2010-01-02
> **drs305 said:**
> In Karmic you also have System > Administration > Disk Utility, which provide information and the ability to do some basic tasks like set labels.

It appears to me that the SD media is not mounted.

I did have the card out and using it in a camera for a bit.

I have a dual boot system and Windows does see the SD card. But, no where to be found in Ubuntu.

How do I format and get this SD card properly mounted??

Thanks again

---

### Post by drs305 on 2010-01-02
Run these commands to see if Ubuntu even sees the device and card.
```

lsusb

```

My cardreader returns the following:
> 
Bus 001 Device 006: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)


If your system recognizes the card reader, next try this with the card inserted to see if the system sees the SD card:
```

sudo fdisk -l

```
My result:
> 
/dev/sdd1               1        4023      502667+   6  FAT16


I don't know if SD cards are subject to problems if removed improperly, but you might try putting it back into Windows and making sure to safely unmount the device. (Windows users please provide input on this).

Once we know that Ubuntu can see the reader *and* the card, we can try to mount it either manually via command line or add an entry to fstab (although it should mount automatically). Then once we know it is mountable we can try to discover why it isn't mounting automatically when inserted.

---

### Post by padrejeff on 2010-01-02
OK,

If I insert the SD card into my card reader and then insert the card reader into a USB, the SD card shows up immediately on the Desktop.

It then can be opened by double clicking and the File Browser shows everything on the card.

If I right click, it shows an "Unmount Volume" in the drop down menu (which tells me it is automatically mounting it when it is inserted.

Now, why does it not show up at all when inserted into the SD card slot on my Mini?


Jeff

---

### Post by drs305 on 2010-01-02
> **padrejeff said:**
> Now, why does it not show up at all when inserted into the SD card slot on my Mini?

We've established that the card doesn't have any problems and that your system is set up to properly automount an SD card when recognized. So the problem would appear to be with your Mini's card reader.

Does the internal card reader show up as a listed device when you run the "lspci" command?

---

### Post by padrejeff on 2010-01-02
> **drs305 said:**
> We've established that the card doesn't have any problems and that your system is set up to properly automount an SD card when recognized. So the problem would appear to be with your Mini's card reader.

Does the internal card reader show up as a listed device when you run the "lspci" command?

If, in Terminal, I simply type:

ispci

I get this:

bash: ispci: command not found
jeffjohnston@ubuntu:~$

Don't know what that means?

Jeff

---

### Post by megamania on 2010-01-02
> **padrejeff said:**
> If, in Terminal, I simply type:

ispci

I get this:

bash: ispci: command not found
jeffjohnston@ubuntu:~$

Don't know what that means?

Jeff
the first letter is a lowercase L, so the command is **l**spci.

---

### Post by durand on 2010-01-02
It's probably because the drivers for your dell mini's card reader either haven't been written or aren't installed on ubuntu.

On my dell laptop, I get something like this from lspci:
```

08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```
If yours is similar, you can follow this guide which should get it working.
[http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu/](http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu/)

---

### Post by padrejeff on 2010-01-02
Sorry,

OK, with lspci, I get this:

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
02:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
02:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
jeffjohnston@ubuntu:~$

---

### Post by durand on 2010-01-02
Did a bit of googling, and it seems like that card reader causes quite a lot of problem on linux. It's probably just best to wait for ubuntu to support it as you already seem to have a working external card reader.

---

