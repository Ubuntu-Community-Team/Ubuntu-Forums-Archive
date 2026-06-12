---
title: "Installing Windows 7 from a Flash Drive"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by alanfang on 2009-06-09
I am running ubuntu, how do I format my flash drive in ubuntu so that I can install the windows 7 ISO? Thanks for the help.

---

### Post by unmole on 2009-06-09
From what I understand you have the DVD image (.iso file) for Windows 7. I doubt if one can use it to boot from a USB device. Insted burn the image to a DVD and then restart the computer and set your BIOS to boot from the DVD. After that you are on your own. I am sure thre are a lot of tutorials to help you from there on. 


P.S. Tell me if this is what you wanted or did I misunderstand ?

---

### Post by alanfang on 2009-06-09
> **unmole said:**
> From what I understand you have the DVD image (.iso file) for Windows 7. I doubt if one can use it to boot from a USB device. Insted burn the image to a DVD and then restart the computer and set your BIOS to boot from the DVD. After that you are on your own. I am sure thre are a lot of tutorials to help you from there on. 


P.S. Tell me if this is what you wanted or did I misunderstand ?

I don't have a DVD drive so that isn't possible. It is possible to install from a flash drive, but the only directions I can find format it under XP/Vista.

---

### Post by uljanow on 2009-06-09
You could use qemu to install Windows on your real hard disk. I've done that with Vista.

---

### Post by Bölvaður on 2009-06-09
you probably will not be able to do what you are trying to do.

But how to format?

push [this link]("apt:gparted")

(or in terminal : sudo apt-get intsall gparted... or go to synaptic and look for gparted)

Then go to System &#8594; Administration &#8594; Partition Editor
Select the flash drive from the drop down list of hdd's connected to your computer. I have 2 hard disks, so when I connect my flash drive in it appears as the third one, C.

Then just right click the partition and select "Format to" and have it ntfs or fat32

---

### Post by unmole on 2009-06-09
Uljanow's  method is probably your best bet. But do you have enough RAM ?

---

