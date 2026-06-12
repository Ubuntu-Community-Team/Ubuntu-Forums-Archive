---
title: "cannot boot from usb flash drive"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by kavoura on 2008-12-19
I created a USB startup disk successfully, using Ubuntu 8.10 AMD64 CD ISO and a 16 GB flash drive.

But my PC will not boot from it. I tried 4 different options for the first boot device: USB-FDD, USB-ZIP, USB-CDROM, USB-HDD. None allowed it to boot. All that happened was that it got as far as "Verifying DMI pool data..." message, and then froze. So it seems that it is reading the USB flash drive, but it will not boot from it.

What could be wrong?

---

### Post by shifty_powers on 2008-12-19
not all usb drives can be used to boot from...

---

### Post by kavoura on 2008-12-19
> **shifty_powers said:**
> not all usb drives can be used to boot from...

So how do I know which ones are bootable and which ones are not? Or is there a way to make them bootable? 

Why do you say that not all USB drives are bootable?

---

### Post by Michaelg14 on 2008-12-19
Some BIOS's will allow you to select a boot menu.  On my AMI bios I can hit f8 and it will come up with a menu that lets me select which boot device I want to use.

---

### Post by kavoura on 2008-12-21
I have now found a Live USB creator at
[http://linux.softpedia.com/get/System/Installer-Setup/Ubuntu-LiveUSB-39755.shtml](http://linux.softpedia.com/get/System/Installer-Setup/Ubuntu-LiveUSB-39755.shtml)

I have created my live USB Ubuntu flash drive, which is certainly now bootable, so nothing wrong with the drive itself. But, it had an error when booting about not finding the linux kernel. I will have to investigate further when I have the time, but at least I know that the flash drive is bootable. 

But I do not see why the Ubuntu program to create a USB startup disk did not work in making the flash drive bootable, whereas the "Install Live USB" program which I used did make it bootable. I also noticed that this latter program divides the flash drive into two partitions, which makes more sense than the Ubuntu startup program, so that there is a main bootable partition and a second partition for the home directory and files which is persistent.

---

### Post by kavoura on 2008-12-25
I am still having problems with the bootable USB flash drive I am trying to create. It still will not boot, it gives an error saying that it cannot find the linux kernel image. I compared the contents of the drive with the Ubuntu 8.10 CD and saw that the CD had more directories than the flash drive, so I copied those over to the flash drive.

But it still does not boot, so still something must be missing.

Attached is a list of directories and files on the flash drive

---

### Post by albinootje on 2008-12-25
> **kavoura said:**
> I created a USB startup disk successfully, using Ubuntu 8.10 AMD64 CD ISO and a 16 GB flash drive.

But my PC will not boot from it. I tried 4 different options for the first boot device: USB-FDD, USB-ZIP, USB-CDROM, USB-HDD. None allowed it to boot. All that happened was that it got as far as "Verifying DMI pool data..." message, and then froze. So it seems that it is reading the USB flash drive, but it will not boot from it.

What could be wrong?

I have different results with different usb-sticks and different machines.
Machines which claim to support usb booting would not boot :( while I tested it successfully at home.

Here's other software to try : [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by tatojo on 2008-12-25
Did you try [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) ?
I used 
Automatic Approaches

UNetbootin (GUI-based, runs from either Windows or Linux)

From a amd64 to create a Kingston DataTraveler 2Gb usb, to install Ibex in my AcerAspireOne (of course, after download the iso), and worked fine.

---

