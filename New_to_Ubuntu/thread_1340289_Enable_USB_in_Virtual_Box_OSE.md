---
title: "Enable USB in Virtual Box OSE"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by dilantha on 2009-11-28
Hi everyone,
 I just need some help with enabling USB  in my virtual box(3.0.8_OSE). I have installed windows XP in my virtual box and everything works perfectly except the USB  ports. i saw some of the articles were mentioned about uncomment some lines of the below file. 

> sudo gedit /etc/init.d/mountdevsubfs.shbut it didn't work for me because /etc/init.d/mountdevsubfs.sh is an empty file :( . If you have had any success with the OSE version and USB, please let us know.Thanks..

---

### Post by howefield on 2009-11-28
> **dilantha said:**
> If you have had any success with the OSE version and USB, please let us know.

As far as I am aware, only the PUEL version of Virtualbox has support for USB, not the OSE version in the repository.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by halitech on 2009-11-28
Virtualbox OSE does not support using USB devices. You need the closed source edition

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by andrew.46 on 2009-11-29
Hi dilantha,

As previous posters have pointed out you need the Puel edition rather than OSE. Mind you I run the OSE version and I access my usb external drive from the guest OS by the simple hack of placing a symbolic link to the drive into a shared folder. A nice little trick?

All the best,

Andrew

---

### Post by dilantha on 2009-11-29
> **howefield said:**
> As far as I am aware, only the PUEL version of Virtualbox has support for USB, not the OSE version in the repository.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

Hi,
:(..Well then i will have to remove my existing virtual box and reinstall the PUEL version..But any way thanks a lot for your help..:D

---

### Post by dilantha on 2009-11-29
> **andrew.46 said:**
> Hi dilantha,

As previous posters have pointed out you need the Puel edition rather than OSE. Mind you I run the OSE version and I access my usb external drive from the guest OS by the simple hack of placing a symbolic link to the drive into a shared folder. A nice little trick?

All the best,

Andrew

Hi Andrew,
 
 :) Yeah..That's a cool trick. Thanks a lot..But when it comes to USB devices like Web cam ect.. i think its better to go for Puel edition. anyway Thanks a lot guys..really appreciate your help.. :guitar:

---

### Post by bunty on 2010-11-23
@andrew.46

Thanks for this tip. The web is minging with "knowledgable" replies about you can't do it and I was sure there must be a work around. 

You are not very explicit but am I right in thinking that you mean that you have to set up a directory to be shared between the VM and the host then mount the USB device and create a symlink on the host system?

I'm sure there must be some trick with pipes and redirection to get other devices to work too. I'm just having trouble filtering out the millions of search results for people who did not read the basic difference between the OS and closed source versions. 

The added benefit of the OSE version is it has VNC server which PUEL can't use because of license conflicts. 

Disks and USB sticks are an obvious need , usb printers are another. I suppose one option would be to print to a file in a shared directory and the reprint it from CUPS on the host. 

Obviously Sun (now Oracle) are using this pretty fundament lack of function to differentiate their marketing strategy but I'm surprised no one had simply written an opensource VB kernel module or whatever is needed to get this functionality added.

Since there is full source for OSE and the std USB stuff it would not seem like an insurmountable problem. I'm sure some hacker must have done it it just for the fun.

---

