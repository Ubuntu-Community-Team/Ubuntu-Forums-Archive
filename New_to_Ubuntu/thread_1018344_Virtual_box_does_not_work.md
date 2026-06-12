---
title: "Virtual box does not work"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by tusherr on 2008-12-22
Dear friends,

Just now I have install a virtual box in my Ubuntu. But I could not make it run. I want to access my Windows XP and run adobe photo shop 7 and Dream waver 80. I have created a virtual machine with 300MB RAM and a virtual hard disk image file of 6.0 GB. What should I do now. 

Information if might need to reply:
==================================
Name: Sun xVM Virtual Box
Version: 2.0.6


General
Name:  Coldbox
OS Type:  Windows XP
Base Memory:  192 MB
Video Memory:  8 MB
Boot Order: Floppy, CD/DVD-ROM, Hard Disk
ACPI:  Enabled
IO APIC:  Enabled
VT-x/AMD-V: Disabled
PAE/NX: Disabled
 

PLEASE FEEL FREE TO GIVE ME STEP BY STEP INSTRUCTION TO RUN THIS SOFTWARE. IF NEEDED I WILL START IT FROM THE VERY FIRST...

faisal

---

### Post by sajnox on 2008-12-22
You should install Windows on the virtual machine, you can't access your windows partition from the virtual machine. (Well may be you could, but it's not that simple)

If you want to install windows on a virtual machine you will need a windows install cd and make it the boot option for the virtual machine

---

### Post by jerome1232 on 2008-12-22
You basically have to think of a virtual machine as a whole separate computer, you have all the "hardware" put together now you need to install an operating system on it.

There exists ways to get Virtualbox to use a real hard drive (or at least turn a real partition into an image that virtualbox can use) but they aren't easy.

---

### Post by tusherr on 2008-12-24
> **jerome1232 said:**
> You basically have to think of a virtual machine as a whole separate computer, you have all the "hardware" put together now you need to install an operating system on it.

There exists ways to get Virtual box to use a real hard drive (or at least turn a real partition into an image that virtual box can use) but they aren't easy.

Fist I want to thank you for the reply.

Ok, If you think that is not so easy for me than forgot about it. Just give me a step by step instruction "How can I use Photo Shop (which is installed in windows) in Ubuntu 8.10". Please don ask me to use Wine. Try to help me with Virtual box. If there is no way to use Photo shop without installing in ubuntu than give me Step by Step instructions how can I use it with wine.

current status:
Virtual box installed.
I create an image file of 6 GB
nOW wHAT SUD i DO????

Thank you for cooperation.

---

### Post by albinootje on 2008-12-24
> **tusherr said:**
> 
current status:
Virtual box installed.
I create an image file of 6 GB

Next steps to do :
Put in your MS-Windows cdrom in the cdrom-drive.
Enable the cdrom-drive in your Windows VM in VirtualBox.

---

### Post by st33med on 2008-12-24
Do you have a Windows XP disc? If you do, pop it in the disc drive. In the VBox menu, click on your virtual machine you want to install Windows to, and click settings.  Go to CD/DVD-ROM and Click 'Mount CD/DVD Drive' and 'Host CD/DVD Drive'.  If you only have one CD drive, the correct one should be selected. Click 'OK' and double-click your Windows VM to start it.  Just follow the instructions in order to install.  

Also, if you get to a part where it asks you how to format your HDD, tell it to do Quick Formatting.  You have no data on the virtual HDD, so why bother with the slower one.

---

### Post by HotShotDJ on 2008-12-24
If you need a step-by-step, try these instructions: [https://help.ubuntu.com/community/VirtualBox#Using%20Virtual%20Box](https://help.ubuntu.com/community/VirtualBox#Using%20Virtual%20Box)

---

### Post by Old_Grey_Wolf on 2008-12-24
Edit: removed. What I had linked to was too risky for some new to VBox or Linux.

---

