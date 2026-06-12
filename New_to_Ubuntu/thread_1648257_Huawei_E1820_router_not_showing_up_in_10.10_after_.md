---
title: "Huawei E1820 router not showing up in 10.10 after shutdown without disconnecting."
date: 2010-12-18
forum: New to Ubuntu
---

### Post by The_Librarian on 2010-12-18
[-]Hi there

Earlier this evening I was able to surf using my Huawei E1820 router without any issues. I then performed a shut down without disconnecting the router from the Internet.

Then, when I started the laptop up again later, Ubuntu failed to pick up the E1820 router. I uninstalled and reinstalled usb_modeswitch, hoping that it might fix the problem, but it didn't.

I suspect that there is something which got corrupted as a result of me not disconnecting before shutting down. (All the previous times I have disconnected before shutting down, no issues then).

Where else can I poke my grubby fat finger in to fix things?

lsusb do show that the system is picking up the router, I've also tried the *sudo modprobe option* command as well, but nothing helps.

Kind regards

Ook[/-]

See post below for update.

---

### Post by The_Librarian on 2010-12-29
Update :

I have traced the problem down.

The huawei E1820 dongles have a slot for a microSD card - and I found that when I insert such a card, the E1820 and Windows is cherry, no issues there, but woe betide you if you plug this combination in on Ubuntu 
- this screws up something that Ubuntu is unable to detect the E1820.

This also affect any wifi connections you might have, but this is temporarily though.

Investigation shows the following :

1. Ubuntu system picks up the vanilla E1820. You can then surf and do whatever you want.
2. After adding a 2Gb microSD card, and plugging it into the same Ubuntu system as in 1, you'll find that Ubuntu doesn't pick the router up at all, although it is indeed present and correct when doing an lsusb and dmesg|grep -i 'huawei'
 3. Removing said microSD card, and plugging the router into another Ubuntu system verifies that the router still is working.
4. Putting the router back on the original Ubuntu system (1) proves to be fruitless as it still is not detected correctly.

In light of the above, I suspect that some configuration file might be corrupt - but is not sure where to look.

Here's the output of dmesg|grep -i 'huawei'

```

[   51.486560] scsi 5:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   51.491043] scsi 6:0:0:0: Direct-Access     HUAWEI   TF CARD Storage       PQ: 0 ANSI: 2
[  358.477881] scsi 10:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  358.503370] scsi 11:0:0:0: Direct-Access     HUAWEI   TF CARD Storage       PQ: 0 ANSI: 2
[  463.934618] scsi 14:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  463.959075] scsi 15:0:0:0: Direct-Access     HUAWEI   TF CARD Storage       PQ: 0 ANSI: 2

```and of lsusb

```

Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1267:0201 Logic3 / SpectraVideo plc A4Tech SWOP-3 Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 013: ID 12d1:14ac Huawei Technologies Co., Ltd. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Regards

Ook

---

