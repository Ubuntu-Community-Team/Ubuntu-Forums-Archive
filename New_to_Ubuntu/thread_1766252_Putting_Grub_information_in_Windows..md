---
title: "Putting Grub information in Windows."
date: 2011-05-24
forum: New to Ubuntu
---

### Post by Nixot on 2011-05-24
Hello everyone

I've got Windows on the hard drive and have Ubuntu on a USB stick, and I want to have Grub running on the hard drive, even when I unplug the USB stick.
When I unplug the USB stick, the computer doesn't boot because the grub data 'n' stuff is on the USB stick.
(it's a tablet computer so I can't install grub on the USB stick and press F2 to change the boot order).

Can I install Grub in such a way that both the boot loader and the grub data will be on the hard drive (even though it runs Windows)?
Thanks for any help

---

### Post by Hedgehog1 on 2011-05-24
You other option is to make the hard drive boot into windows, and then you can manually select the Ubuntu USB where you want to boot form it.

To make the hard drive boot into windows, you need to the a 'fixmbr':

[SIZE="3"]Fix MBR[/SIZE]

To get your PC to boot directly into Windows again:

To make a Windows 7 / Vista emergency repair disk (in case you don't already have one made):
[IMG]http://img641.imageshack.us/img641/9550/small50createrepairdisk.png[/IMG]

If you are unable to make a recovery disk, you can download the ISO for [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

---

### Post by Nixot on 2011-05-24
I already said, I can't pick between booting normally and into the USB stick, because I'm on a tablet computer and there's no buttons to enter or use the setup.

---

### Post by _0R10N on 2011-05-24
There's something I don't get. What are you trying to achieve? installing Ubuntu along with Windows? If so, then you can boot to windows and then use the wubi installer. It will take care of all the details concerning to disk administration, boot set up, etc.

regards!

---

### Post by coffeecat on 2011-05-24
> **Nixot said:**
> Hello everyone

I've got Windows on the hard drive and have Ubuntu on a USB stick, and I want to have Grub running on the hard drive, even when I unplug the USB stick.
When I unplug the USB stick, the computer doesn't boot because the grub data 'n' stuff is on the USB stick.
(it's a tablet computer so I can't install grub on the USB stick and press F2 to change the boot order).

Can I install Grub in such a way that both the boot loader and the grub data will be on the hard drive (even though it runs Windows)?
Thanks for any help

This is theoretically possible, but you would need a dedicated partition on the hard drive for some of the grub code.

The way grub normally works is that there is grub code (about 440 bytes only) in the mbr and then some more in the embedding area, which is a normally unused section of the hard disc between the partition table and the first sector of the first partition. The main challenge for what you propose is that the rest of the grub code responsible for booting, including the grub.cfg file, is in /boot/grub of your Linux root partition, or boot partition if you have one. You would need to create a small partition especially for the files that normally go in /boot/grub. Quite how you would do this, I don't know. The other problem is that to generate the grub.cfg file, you need the various grub application and configuration files scattered around in /usr and /etc. It should be possible, and I'm sure someone's done it, but I wouldn't know how to go about achieving this - at least not without a lot of thinking.

If I find something, I'll post back.

---

### Post by oldfred on 2011-05-24
I have installed grub2 to a FAT formated USB windows repair CD and it works. But you do not get all the other bits that are part of the Ubuntu install that include os-prober and settings to create a grub.cfg file. You have to manually create a grub.cfg file with windows and your USB entries. With win7 you will have to be careful to not create two /boot folders. Windows is not case sensitive and /boot and /Boot are the same and then windows does not work. Not sure if grub uses /boot or /Boot but it needs to be in the same folder as your existing /boot that has the essential BCD file.

This is my grub.cfg and I am also loopmounting ISO repairCDs as well as the win repair install. (not updated to newer ISO I see).

```
menuentry "Microsoft Windows Recovery" {
      set root=(hd0,1)
      chainloader --force +1
}

menuentry " " {
set root= 
}

menuentry "ubuntu-9.10-desktop-i386.iso" {
    set isofile="/ISO/ubuntu-9.10-desktop-i386.iso"
    insmod ext2
    loopback loop (hd0,2)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}

```[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-install")

Edit 

It would be much better to have a separate grub2 boot partition, so you do not have issues of mixed windows & grub files/folders.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

### Post by beew on 2011-05-24
Why do you want the grub data to be on the hard drive even when the usb is not plugged in?
It seems that you are making things unnecessarily complicated.

If I were you I would have installed grub in the usb during installation and left the internal hard drive alone (choose manual partition during install even if you don't intend to create multiple partitions in the usb, that way you have the option to choose where to install grub. If you chose the automatic options grub would be installed in the internal drive so you wouldn't be able to boot into Windows if the usb is unplugged)

So, if the usb is not plugged in you boot normally into windows. If the usb is plugged in (and BIOS configured to boot from usb) then you have choice to either boot into windows or Ubuntu.

P.S. I assume you have done a full installation into an USB drive rather than running a live usb or doing something funny like WUBI. Running Ubuntu off usb is slow, you get much better performance by installing in an external hard drive instead.

---

### Post by aphatak on 2011-05-24
An alternative would be to use Windows bootloader to give you a choice between Windows and Grub - you can find a how-to article at "http://oreilly.com/pub/h/2337".  That way, your bootloader will always be on the hard drive, and you could choose to go into Grub (and then Linux) when you want to load Linux from the USB drive.

---

### Post by Nixot on 2011-05-25
> **_0R10N said:**
> There's something I don't get. What are you trying to achieve? installing Ubuntu along with Windows? If so, then you can boot to windows and then use the wubi installer. It will take care of all the details concerning to disk administration, boot set up, etc.

regards!

Because, with Wubi you are not able to hibernate, and if you hibernate windows you will not be able to boot into Ubuntu at all.

> **beew said:**
> Why do you want the grub data to be on the hard drive even when the usb is not plugged in?
It seems that you are making things unnecessarily complicated.

If I were you I would have installed grub in the usb during installation and left the internal hard drive alone (choose manual partition during install even if you don't intend to create multiple partitions in the usb, that way you have the option to choose where to install grub. If you chose the automatic options grub would be installed in the internal drive so you wouldn't be able to boot into Windows if the usb is unplugged)

So, if the usb is not plugged in you boot normally into windows. If the usb is plugged in (and BIOS configured to boot from usb) then you have choice to either boot into windows or Ubuntu.

P.S. I assume you have done a full installation into an USB drive rather than running a live usb or doing something funny like WUBI. Running Ubuntu off usb is slow, you get much better performance by installing in an external hard drive instead.

If I unplug and re-plug the USB drive I won't be able to press F2 to configure the boot order again because I am on a tablet. Having the boot loader on the main disk will allow me to boot into windows if the USB isn't plugged in, and will allow me to boot into Ubuntu if the USB is plugged in.

> **aphatak said:**
> An alternative would be to use Windows bootloader to give you a choice between Windows and Grub - you can find a how-to article at "http://oreilly.com/pub/h/2337".  That way, your bootloader will always be on the hard drive, and you could choose to go into Grub (and then Linux) when you want to load Linux from the USB drive.

This seems like the most logical answer and I will give it a go tomorrow when I have finished my exams.

---

