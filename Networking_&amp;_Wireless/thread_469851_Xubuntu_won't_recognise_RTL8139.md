---
title: "Xubuntu won't recognise RTL8139"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by Robsteranium on 2007-06-10
I've just installed xubuntu.  All my other hardware seems to have been identified automatically.  My xubuntu box will ping localhost but everything else is unreachable!  I've used WinXP on the same machine and the ethernet card works.

I'm using a different pc running xp to post this message: the active LAN can be identified from this end of a twisted net cable so why won't my xubuntu box recognise the card?

The computer won't boot unless I use BIOS setting PNP0S=NO (otherwise it hangs when detecting the ethernet card).  In cases this is relevant: upon booting I receive (and ignore!) the "ACPI unable to locate RSDP" error.

None of the dialogs in applications>system>network are any use because no ethernet card is found.  Ifconfig replies with the loopback alone.

I've tried modprobe 8139too and lsmod | grep 8139 confirms this has added the driver.  This doesn't seem to help and it's disappeared on a reboot.

I can't get anything from
```
lspci | grep -i ethernet
dmesg | grep eth
lshw -C network
```

If I try dhclient eth0 it says "no such device".

Any ideas?

---

### Post by Robsteranium on 2007-06-11
XP identifies my card as a ISA NE2000 compatible.  The following command gets the device driver working:
```
modprobe ne
```
Now I've just got to work out how to enable it...:-k

---

### Post by ugm6hr on 2007-06-11
Just so you know - the card does work out-of-the-box with Xubuntu7.04.

My *lspci*
```
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

As for why you get nothing from lspci - I have no idea I'm afraid.  Did it return anything when you booted from the LiveCD?

---

### Post by Robsteranium on 2007-06-13
I'm beginning to wonder if I've mis-identified the card.
I presume lspci doesn't pick it up because my decrepit NIC uses an ISA socket.

---

