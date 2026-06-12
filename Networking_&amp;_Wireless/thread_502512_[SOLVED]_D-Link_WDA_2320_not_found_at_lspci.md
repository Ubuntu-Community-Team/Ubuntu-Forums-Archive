---
title: "[SOLVED] D-Link WDA 2320 not found at lspci"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-07-16
Why me, Oh Lord?

Opened the box from D-Link with WDA 2320 in it. Turned the computer off, unplugged the power cord. Installed the card. One LED blinks green.

lspci shows it's not there.

Reading at: Wireless Networking Central

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

sudo pccardctl ident

returns no info.

lspci

shows no card on the bus

the output of 

lshw makes no mention of Atheros or D-link

it does suggest:

append the following to the kernel boot line:

        pci=assign-busses
  
Where is the kernel boot line, and how do I append the line?

Also at madwifi.org, it says I need to install all the following:

linux-restricted-modules-2.6.20-15-386

linux-restricted-modules-2.6.20-15-lowlatency

linux-restricted-modules-2.6.20-16-386

linux-restricted-modules-2.6.20-16-generic

linux-restricted-modules-2.6.20-16-lowlatency

Can I place these devices on a thumb drive and use the Archive Manager to properly install them? Also do I need the -15 and -16 modules? Shouldn't the -16 be better?

---

### Post by Mark_in_Hollywood on 2007-07-16
I took a big chance and added that line to the grub file. Rebooted. Nothing.

---

### Post by kevdog on 2007-07-17
First find your kernel version
```
uname -r
```

This will refer to the version you have to edit.

Below is an example.  Please note that your kernel version file may be different
okay ... let's add a couple of kernel options to try to avoid that irq conflict.

first backup your grub like so:
> 
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup

now, if your computer won't boot after the changes, just use the live cd and move the menu.list-backup to menu.lst

find your most recent kernel line. it should look something like this:
> 
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash

Now add something like the following:


```
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash pci=assign-busses
```

Another example may be the following:
```
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=70d0a61f-7453-46d4-85ad-1373ef99813a ro quiet splash noapic nolapic pci=assign-busses
```

---

### Post by Mark_in_Hollywood on 2007-07-17
OK

I found the correct boot file lines in menu.lst, tried them both, the both hung the x server. I returned the menu.lst lines to as they had been and the system is back to normal.

---

### Post by Mark_in_Hollywood on 2007-07-20
The card was bad. it has been replaced with another WDA 2320 and it is working. list of lspci shows it on the bus.

many thnx.

---

