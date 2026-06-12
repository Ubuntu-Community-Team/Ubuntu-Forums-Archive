---
title: "can't get virtual box working"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by mike101 on 2010-03-16
Hello

I'm new to Linux. 

I'm trying to get virtualbox to run with Ubuntu as the host and Windows guest.

I've installed Virtualbox but my Windows OS (Vista) is just on the hardrive (I don't have a disc). How do I get Vista into Virtualbox?
Can I burn it to a CD? If so which files do I select?

Thanks in advance for any help

---

### Post by yeats on 2010-03-16
Hello and welcome.

You need an installation disc for Vista and what you install in VBox will be considered by Microsoft to be a separate machine (meaning you will need to "re-buy" Vista to install it in VBox).  If you are wiping Vista from your hard drive and reinstalling it in VBox, you can call Microsoft and tell them that you are installing your purchased copy onto a new machine and they will give you an activation code.

---

### Post by thegod_slayer on 2010-03-16
you just need to install vbox first in your system.
then create a vmachine having a certain size like 1 gb or something
then just install vista or whatever os you want in your newly created vmachine
in the same way you would install it into an original rig.

---

### Post by mike101 on 2010-03-16
Hello

> **chrissharp123 said:**
> Hello and welcome.

You need an installation disc for Vista and what you install in VBox will be considered by Microsoft to be a separate machine (meaning you will need to "re-buy" Vista to install it in VBox).  If you are wiping Vista from your hard drive and reinstalling it in VBox, you can call Microsoft and tell them that you are installing your purchased copy onto a new machine and they will give you an activation code.

Yes this is what I want to do- but I'm a little confused.
How do I wipe Vista from my hard drive and install it in Vbox?

---

### Post by howefield on 2010-03-16
Have a look at this tool to create a vm from your existing windows install, Virtualbox will be able to use the VHD file created.

[http://technet.microsoft.com/en-us/sysinternals/ee656415.aspx](http://technet.microsoft.com/en-us/sysinternals/ee656415.aspx)

---

### Post by ibuclaw on 2010-03-16
Have a look here for loose documentation: [http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

Also, not to step on your shoes, but I entrust that your version of windows is licensed to run in a virtual machine?

Regards
Iain

---

### Post by alboreira on 2010-03-16
You can download a Windows ISO file from MSDN, create a new VM in VirtualBox and install Windows in your VM from that ISO file. I do that all the time in my VM class at school. I believe Microsoft gives you a 3 month grace period for evaluation, and I was also told that there's a way of extending that period to 6 months, so, I don't think you even need a product key to play with a Windows VM. 

However, if you want to use Windows for more than 6 months, you will need to buy a copy. And I would seriously consider Windows 7 instead of Vista. 

However, I'm not sure if VirtualBox can virtualize Windows if your machine doesn't have the hardware virtualization extensions, such as Intel VT or AMD-V. My machines do, both at home and at school, I'm a 64-bit user. Also, even if your machine has the extensions, you may need to boot into the Bios Setup and turn them on, because they usually come turned off by default. 

Hope this helps!

Alberto.

---

### Post by sandyd on 2010-03-16
> **alboreira said:**
> You can download a Windows ISO file from MSDN, create a new VM in VirtualBox and install Windows in your VM from that ISO file. I do that all the time in my VM class at school. I believe Microsoft gives you a 3 month grace period for evaluation, and I was also told that there's a way of extending that period to 6 months, so, I don't think you even need a product key to play with a Windows VM. 

However, if you want to use Windows for more than 6 months, you will need to buy a copy. And I would seriously consider Windows 7 instead of Vista. 

However, I'm not sure if VirtualBox can virtualize Windows if your machine doesn't have the hardware virtualization extensions, such as Intel VT or AMD-V. My machines do, both at home and at school, I'm a 64-bit user. Also, even if your machine has the extensions, you may need to boot into the Bios Setup and turn them on, because they usually come turned off by default. 

Hope this helps!

Alberto.
30 Days evaluation to be exact.

---

### Post by yeats on 2010-03-16
> Yes this is what I want to do- but I'm a little confused.
How do I wipe Vista from my hard drive and install it in Vbox?

It will be a new installation - you won't be able to take what you have installed now and drop it directly into VirtualBox.  The best you can do is back up all your Windows files and settings, then use gParted or some other tool to delete the Windows partition (assuming that you use GRUB to boot here - if you use Windows' bootloader you'll want to install and use GRUB instead before removing anything).  Then you can create a VirtualBox disk of the desired size and reinstall Vista from there.

---

