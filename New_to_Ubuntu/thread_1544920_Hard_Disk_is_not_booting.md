---
title: "Hard Disk is not booting"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by pirate omar on 2010-08-03
after installing Ubuntu 10.04 from a USB stick successfully
can not boot from the hard disk, but if i plug the USB Stick it will boot normally from the hard drive
I used the whole hard drive as one ext4 partition
please help

---

### Post by giddyup306 on 2010-08-03
> **pirate omar said:**
> after installing Ubuntu 10.04 from a USB stick successfully
can not boot from the hard disk, but if i plug the USB Stick it will boot normally from the hard drive
I used the whole hard drive as one ext4 partition
please help


Go into BIOS and make sure that your computer is set to boot off the hard drive.  With the stick there is a chance that it's only looking for the USB device.

---

### Post by pirate omar on 2010-08-03
I already tried, I guess its a boot sector matter

---

### Post by tarps87 on 2010-08-03
Could you be more descriptive please, do you see any error messages?

---

### Post by pirate omar on 2010-08-03
after a successful installation of Ubuntu
- booting from hard disk give a (missing operating system) error
- booting from memory stick (Bootable Ubuntu installation image) will boot normally from hard disk after a couple of seconds waiting time

---

### Post by Zimmer on 2010-08-03
During install you will have installed GRUB2. And you probably did not select the  'Advanced ' option . It is likely that GRUB2 installed to the MBR of the USB stick, not the Hard Drive.
It should be possible to recover by re installing GRUB to the Hard Drive.
If you can boot from CD use a LiveCD of 10.04 

If  not, put the USB drive in place and boot into Ubuntu.
Check what the disks are mounted as from a terminal with 
sudo fdisk -l   (that is a lowercase L !)
It is most likely the Ubuntu install is on your hard drive and that is recognised as  /dev/sda

See
[http://members.iinet.net.au/~herman546/p20/GRUB2%20Bash%20Commands.html#install_update_and_repair](http://members.iinet.net.au/~herman546/p20/GRUB2%20Bash%20Commands.html#install_update_and_repair)

and from that you will gather that you should try 

sudo grub-install /dev/sda 
to install GRUB2 to your Hard drive. Reboot with USB removed...

---

### Post by tarps87 on 2010-08-03
> **pirate omar said:**
> after a successful installation of Ubuntu
- booting from hard disk give a (missing operating system) error
- booting from memory stick (Bootable Ubuntu installation image) will boot normally from hard disk after a couple of seconds waiting time

This leads me to the same conclusion as Zimmer,  installing grub to the hard drives MBR (master boot record) should solve you issue. See Zimmers post above

---

### Post by pirate omar on 2010-08-04
> **Zimmer said:**
> During install you will have installed GRUB2. And you probably did not select the  'Advanced ' option . It is likely that GRUB2 installed to the MBR of the USB stick, not the Hard Drive.
It should be possible to recover by re installing GRUB to the Hard Drive.
If you can boot from CD use a LiveCD of 10.04 

If  not, put the USB drive in place and boot into Ubuntu.
Check what the disks are mounted as from a terminal with 
sudo fdisk -l   (that is a lowercase L !)
It is most likely the Ubuntu install is on your hard drive and that is recognised as  /dev/sda

See
[http://members.iinet.net.au/~herman546/p20/GRUB2%20Bash%20Commands.html#install_update_and_repair](http://members.iinet.net.au/~herman546/p20/GRUB2%20Bash%20Commands.html#install_update_and_repair)

and from that you will gather that you should try 

sudo grub-install /dev/sda 
to install GRUB2 to your Hard drive. Reboot with USB removed...


Thanks Zimmer, Thanks guys, it worked
my hard drive was /dev/sdb because the USB stick was /dev/sda

---

