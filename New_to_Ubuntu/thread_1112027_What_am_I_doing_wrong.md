---
title: "What am I doing wrong?"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-03-31
I did this guide to transfer my live cd iso image to my IDE 2 gig solid state disk.

my computer automatically puts in /dev/sda 
I format my /dev/sda1 to fat 16

so I do this commands


sudo umount /dev/sda1

sudo fdisk /dev/sda1

sudo syslinux -sf /dev/sda1

mkdir /dev/shm/myiso

sudo mount -o loop /home/eric/ubuntu-8.04.2-desktop-i386.iso /dev/shm/myiso

cd /dev/shm/myiso

sudo cp -rfv casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz /media/disk/


#this is for the boot menu to be changed to only 1 option.
cd /media/disk
cp isolinux.cfg syslinux.cfg
cp isolinux.txt syslinux.txt

now my solid state disk saids it looks ok.

I mean it has like 700 mbs worth of file space (which is the iso image estimate amount)

and its bootable and all that i did the fdisk properly (lots of times.)

i got the syslinux tool

it looks ok all the .cfg and .txt files are correct and looks like eeverything on it. and my bios has harddrive first and usb enabled. but it wont boot up no matter what.

What the hell is wrong :( im stumped anyone help? it will be much appreciated.

---

### Post by Kosimo on 2009-03-31
The question that comes up to my mind is: 
Why don't you use the automatic USB-Stick creator included in Intrepid?

---

### Post by ericeclifford on 2009-03-31
I dont know ill try it out, I found somthing on pendrive.com and ill see if this helps if not ill try it that way and report back the results.

---

### Post by ericeclifford on 2009-03-31
Well I have 8.04.2 first, so I downloaded the usb creator , and it doesnt pick up my solid state disk, probably because its not a usb

anyone got any suggestions or advice?

---

### Post by ibuclaw on 2009-03-31
Unetbootin is a brilliant tool for this:
[https://launchpad.net/~gezakovacs/+archive/ppa](https://launchpad.net/~gezakovacs/+archive/ppa)

Regards
Iain

---

