---
title: "Ubuntu on USB flash stick - data doesn't persist."
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Minolas on 2009-01-10
Hi.

I'm new into Ubuntu.

I used the unetbootin-windows-304.exe program and selected the file 'ubuntu-8.10-desktop-i386.iso', then chose my USB Stick in order to make my 16Gb USB Stick with Ubutu bootable.

USB Stick boots fine and all that. I have 2 partitions on the USB Stick, 1st one 1Gb FAT16 and second one 15Gb FAT32.

So far so good.

Problem: When I am installing software on the Ubuntu like VMPlayer it installs just fine and I can run it. But the Data doesn't presist. That is the next time I boot I have to install programs again. It seems as if it installs them into ramdisk or something although I am using a USB Stick which obviously is read/write.

How can I make the bootable USB save changes and allow to install programs ? Seems like an easy question but I was unable to find why the hell Ubuntu doesn't see that it's USB Stick and allows it to also save data.

Thanks a lot
Minolas

---

### Post by markg48 on 2009-01-10
why dont u use wubi  ubuntu default install inside windows option ?

plus there an option  when you boot live cd in the meneus  create usb start up disk i think it install ubuntu on usb not sure i have never used that option though

wubi would be easier to use though.... sit in inside a windows partition and can be removed easly   with an uninstall option

---

### Post by Captain_tux on 2009-01-10
> **markg48 said:**
> wubi would be easier to use though.... sit in inside a windows partition and can be removed easly   with an uninstall option

That is correct, however, it defeats the purpose of having Ubuntu installed on an easily portable device.

Under Intrepid, click on **System > Administration > Create a USB startup disk**. While installing, select the option **Stored in reserved extra space** and adjust the slider to set capacity to use (that's what creates the persistence file).

I've created a few USB sticks like this and works like a charm. Here's a little more reference: [http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/)

Buena suerte!

---

### Post by Minolas on 2009-01-10
> **Captain_tux said:**
> That is correct, however, it defeats the purpose of having Ubuntu installed on an easily portable device.

Under Intrepid, click on **System > Administration > Create a USB startup disk**. While installing, select the option **Stored in reserved extra space** and adjust the slider to set capacity to use (that's what creates the persistence file).

I've created a few USB sticks like this and works like a charm. Here's a little more reference: [http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/)

Buena suerte!

Hey thanks a bunch for the solution. I guess I'll have to get the XUbuntu Intrepid and do what you say. But I have two questions please:

1. If I use a 16GB Flash stick with one 16gb partition would it still be able to boot from the USB Stick? Or is there a lower limit?

2. Will I be able to access the drive from Vista ? As I need to frequently move files. I wonder if Vista will be able to recognize and copy files to the USB flash.

Update: I created that USB Stick. I selected to make the persistent space to the rest of the USB stick, something like 15GB (as the OS takes about 1GB). Now I have a parition with about 5GB taken. 1GB the OS and 4GB a file named casper-rw I have tried to search for the forums what that file means but not completely understood it. Is that the file that keeps data ? Then why it's only 4GB while during the creation of the USB stick I actually marked that I want the presistence to be 15GB ? I am confused.

What I am trying to accomplish is very simple:
Ubuntu USB Flash stick with some programs and also a VMPlayer and I need about 10Gb free on the stick so that I could copy a VMWare file which I can also update from other OS like Vista. I'm not sure if what I did during the creation of the USB was right ? Maybe I need to create the USB Boot with just about 1GB of Persistence memory and still be able to put every a large VMWare virtual machine file of like 13gb which I can work on from both the Ubuntu and Vista.

Clarification will be greatly appreciated.

Thanks

---

### Post by Captain_tux on 2009-01-10
To answer your questions...

1. Yes, that is precisely what the tool is designed to do. Is there a lower limit? Perhaps, but as with any drive, the more space you have allocated for it, the better it performs. I only have an 8GB.

2. I've never had to access files on the USB from Vista (so I don't know if you'll be able to), but I do know that you can access it from Ubuntu/Linux just fine. Frankly, I can't see why you can't... Vista should be able to read/write data to it just like any other drive.

The **casper-rw** is the file that allows the persistence. It's hard to mess up the installation, so I'm sure what you did was right. Once it's done, it's a fully capable and usable K/U/Xubuntu installation as if it was installed to a regular hard drive... you should be able to install apps just fine.

---

### Post by Minolas on 2009-01-10
> **Captain_tux said:**
> To answer your questions...

The **casper-rw** is the file that allows the persistence. It's hard to mess up the installation, so I'm sure what you did was right. Once it's done, it's a fully capable and usable K/U/Xubuntu installation as if it was installed to a regular hard drive... you should be able to install apps just fine.

Thanks, but I still don't understand, I have a 16gb drive and I chose the persistence to be 15Gb so why is that file **casper-rw** only 4Gb in size? Does it automatically grow if needed?

And also, when I install an application where does it install it? Does it install it in some sort of program files or does it store it encapsulated into this file ?

On one last note, is it possible to change the persistence size AFTER it's already installed on the USB stick ?

Sorry for the questions, Ubuntu seems great, but I am a newbie to it.

---

### Post by Minolas on 2009-01-10
UPDATE:

I created a bootable USB stick as stated here: [http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/)

Chose the persistence to be 15GB (The OS is approx. 1Gb). Wizard finished.

Computer boots Ubuntu fine from USB stick. It asks me if I want to run it without making changes or to install. Obviously I chose to run it from the USB stick.

Ubuntu then boots.

On the desktop I just see 'examples' and 'install'. Going into 'Places' I can see I have 'File System' and it says free space 3.6gb.

There is another drive 'USB Drive' but clicking on it doesn't do anything at all !

Where is the remaining 10GB of my stick? The File System just reports 3.6 free.

I went to GParted and I noticed that the USB Stick is mounted as '/cdrom' and I managed to open it (from terminal) and I saw a folder that I created in Vista. But I just can't do any changes there. I tried editing a text file but it doesn't allow me.

Remember that what I wanted to achieve is to be able to simply put a 10Gb file on the Stick and be able to access it and change it in Ubuntu or if I put it into Vista the same.

Already wasted hours on this one. What's wrong? Please help, getting slowly frustrated from it.

---

### Post by Captain_tux on 2009-01-10
I'm sorry, but I just don't know... I've not looked at a bootable USB with such granularity. Have you tried Google? 

However, you should be able to change the size of the persistence file. It should work just like any other hard drive.

---

