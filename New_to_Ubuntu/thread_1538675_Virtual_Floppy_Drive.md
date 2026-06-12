---
title: "Virtual Floppy Drive"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by cticer on 2010-07-25
I just installed Ubuntu 10.04 yesterday. This isn't the first time for me to use it, but, still, I am not very good with the terminal.

I was writing a hobby operating system under Windows 7. In Windows 7, it was very easy to create a virtual floppy drive, but in Ubuntu, I can't quite figure it out. I have been messing around with .img files. So far, I can write my own bootloader to the file, and then the virtual machine will boot fine, but it can't find the kernel file, so it just hangs.

The requirements for my bootloader are that the floppy must be FAT formatted.

I believe that when I write the bootloader to the image file (using the dd command), it ruins the FAT file system but I am not sure.

So can anybody give me some instructions on how to create a bootable virtual floppy drive that still honors the fat file system?

Any help with this would be greatly appreciated. Thanks.

---

### Post by jmpeer on 2010-07-25
I'd also like to know how to mount virtual floppies, so I guess bump?

---

### Post by cticer on 2010-07-27
Anybody? The help is greatly appreciated.

---

### Post by cjv8888 on 2010-07-27
Do you have a physical floppy drive or not?

---

### Post by cticer on 2010-07-27
> **cjv8888 said:**
> Do you have a physical floppy drive or not?

I don't have a pysical floppy drive.

---

### Post by philinux on 2010-07-27
> **cticer said:**
> I just installed Ubuntu 10.04 yesterday. This isn't the first time for me to use it, but, still, I am not very good with the terminal.

I was writing a hobby operating system under Windows 7. In Windows 7, it was very easy to create a virtual floppy drive, but in Ubuntu, I can't quite figure it out. I have been messing around with .img files. So far, I can write my own bootloader to the file, and then the virtual machine will boot fine, but it can't find the kernel file, so it just hangs.

The requirements for my bootloader are that the floppy must be FAT formatted.

I believe that when I write the bootloader to the image file (using the dd command), it ruins the FAT file system but I am not sure.

So can anybody give me some instructions on how to create a bootable virtual floppy drive that still honors the fat file system?

Any help with this would be greatly appreciated. Thanks.
[http://swiss.ubuntuforums.org/showthread.php?p=9637490](http://swiss.ubuntuforums.org/showthread.php?p=9637490)
[http://ubuntuforums.org/showthread.php?t=570903](http://ubuntuforums.org/showthread.php?t=570903)
[virtual floppy]("http://www.google.com/search?hl=en&q=ubuntu+Virtual+Floppy+Drive&aq=f&aqi=&aql=&oq=&gs_rfai=")

---

### Post by HermanAB on 2010-07-27
Uhmmm, mount -o loop whatever.img /mnt/floppy

---

### Post by beew on 2010-07-27
What is a floppy? :)

---

### Post by cticer on 2010-07-27
I have been able to create images and such. I just cant figure out how to create a bootable image. I can create an image the size of a floppy and then write my own bootloader to it quite easily, but when i try to add other files, the bootloader cannot find them. I assume it is because the file system becomes messed up after I write the bootloader. The bootloader assumes that the Floppy is FAT formatted.

So I guess to rephrase my question... Does anyone know how to write a bootloader to a FAT formatted floppy (virtual or physical) and have the floppy retain the formatting?

I already know how to mount it, but nothing that I try seems to work. :(

---

### Post by cticer on 2010-07-27
I just found this in the Ubuntu Manuals [http://manpages.ubuntu.com/manpages/intrepid/man8/mkdosfs.8.html](http://manpages.ubuntu.com/manpages/intrepid/man8/mkdosfs.8.html)

> **mkdosfs**  can  not  create boot-able file systems. This isn’t as easy as
       you might think at first  glance  for  various  reasons  and  has  been
       discussed a lot already.  **mkdosfs** simply will not support it ;)


So apparently mkdosfs doesn't support the creation of bootable floppies?

---

### Post by cticer on 2010-07-28
Nevermind. I figured it out. I first mount a loop device. Then I write the files to the device. Then I unmount so that the files actually get written to the device. Then I use dd to write the bootsector.

---

### Post by piyush.neo on 2011-01-15
> **cticer said:**
> Nevermind. I figured it out. I first mount a loop device. Then I write the files to the device. Then I unmount so that the files actually get written to the device. Then I use dd to write the bootsector.

I am struggling hard to make a bootloader but i am unable to simulate it...here is my initial thread...
[http://ubuntuforums.org/showthread.php?t=1666381](http://ubuntuforums.org/showthread.php?t=1666381)

Now i have switched to Virtual Box to simulate it.
It will be great if you can tell the steps in detail in order to run bootloader on Virtual box. i have tried to make a bootable flash drive but i don't know where i am getting wrong. VM didn't recognize my iso file to be bootable.
Please give the steps.
Thanks

---

### Post by piyush.neo on 2011-01-15
> **piyush.neo said:**
> I am struggling hard to make a bootloader but i am unable to simulate it...here is my initial thread...
[http://ubuntuforums.org/showthread.php?t=1666381](http://ubuntuforums.org/showthread.php?t=1666381)

Now i have switched to Virtual Box to simulate it.
It will be great if you can tell the steps in detail in order to run bootloader on Virtual box. i have tried to make a bootable flash drive but i don't know where i am getting wrong. VM didn't recognize my iso file to be bootable.
Please give the steps.
Thanks

:Phew
I have successfully run my bootloader :)....now as cticer say am going to have problem when loading kernel image...i just want to know what do he meant by
*Nevermind. I figured it out. I first mount a loop device. Then I write  the files to the device. Then I unmount so that the files actually get  written to the device. Then I use dd to write the bootsector.*

---

