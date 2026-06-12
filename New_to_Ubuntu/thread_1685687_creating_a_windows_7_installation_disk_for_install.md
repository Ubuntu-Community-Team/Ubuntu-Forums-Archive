---
title: "creating a windows 7 installation disk for installation of virtualbox"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by panderohit on 2011-02-11
hi. today i purchased a brand new hp probook 4720s and wish to install Ubuntu 64-bit instead of the preinstalled Windows 7. However I also have an iPhone and would like to still be able to access iTunes through a windows virtual machine (like virtualbox). However, I do not have a windows installation CD/DVD which, I believe, is required to install the virtual machine. Can someone please help me create an installation disk for Windows 7? I cannot bear using Windows for another day. Someone please help. :)
 
So far I have the following:
1. Operating System DVD Windows 7 Professional (32-bit and 64-bit) both of which came with the laptop. However, I do not know what they are and they do not mention if they are installation disks, so I am not sure if they can be used for creating the virtual machine in Ubuntu.
2. Application and driver recovery DVD, which also came with the laptop and I have no idea what this is.
3. Repair Disk Windows 7 32-bit, which I created through windows in an attempt to create an installation disk.
4. Created a system image on my back up hard drive, no idea why I did it. probably just because I could.
 
However, no where does it say that I can create a windows installation disk and the laptop vendor mentioned that the installation disk is not supplied with the laptop.
 
Can someone please help me? 
 
Thanks in advance.

---

### Post by rvchari on 2011-02-11
browse the dvd and see if you find an iso image (for 64 bit or 32 bit) if you find that then u need not create a fresh disk. you can simple copy and paste the iso image on ur home folder or any destination u like in ur hdd.
in virtualbox, choose the cd drive and select this iso image to boot first. your windows installation will show up when u start the virtual machine win7 on ur virtual box.

i did just that !!!

---

### Post by panderohit on 2011-02-11
Hey rvchari,
 
Thanks a lot that was a super quick reply. I browsed through the first DVD (Operating System DVD Windows 7 Professional 32-bit). It did not contain an .iso image. However, it did seem like the installation disk because the computer started prompting me installation questions (like it had when I turned the computer on for the first time earlier today). this DVD contains the following folders:
- boot
- efi
- sources
- support
- upgrade
 
and the following files:
- autorun
- bootmgr
- setup
 
I believe that this may be the installation disk that I need for setting up the windows virtualbox in Ubuntu. Am I right?
 
Thx.

---

### Post by llamakc on 2011-02-11
You are correct. Good luck.

---

### Post by rvchari on 2011-02-11
> **panderohit said:**
> Hey rvchari,
 
Thanks a lot that was a super quick reply. I browsed through the first DVD (Operating System DVD Windows 7 Professional 32-bit). It did not contain an .iso image. However, it did seem like the installation disk because the computer started prompting me installation questions (like it had when I turned the computer on for the first time earlier today). this DVD contains the following folders:
- boot
- efi
- sources
- support
- upgrade
 
and the following files:
- autorun
- bootmgr
- setup
 
I believe that this may be the installation disk that I need for setting up the windows virtualbox in Ubuntu. Am I right?
 
Thx.


so long as it is bootable disk i dont think u should find it problematic. try to point to the setup in ur cdrom drive when u configure virtualbox for win7.

first boot device should be cdrom (virtual drive set up in virtualbox)

---

### Post by aeiah on 2011-02-11
the problem is, HP get their windows licenses for cheap. because of this, there installation disks may be tied to, say, the motherboard. if this is the case then when you try and install it in virtualbox you'd find that it wont work because the installation disk only sees the virtualised hardware.

you probably want to make sure this wont happen before you delete windows 7 off your laptop. you could do this by just downloading the windows version of virtualbox and trying to create a virtual machine using the install DVD.

---

### Post by rvchari on 2011-02-11
> **aeiah said:**
> the problem is, HP get their windows licenses for cheap. because of this, there installation disks may be tied to, say, the motherboard. if this is the case then when you try and install it in virtualbox you'd find that it wont work because the installation disk only sees the virtualised hardware.

you probably want to make sure this wont happen before you delete windows 7 off your laptop. you could do this by just downloading the windows version of virtualbox and trying to create a virtual machine using the install DVD.

this sure is a better option before deleting win7 once for all....
by the way, let win7 be there.... u can shrink the primary particion C to minimal requirement to run win7. install ubuntu on extended partition and make ur machine a dual boot with grub... (or is it that u totally wanna remove windows from ur hdd?)

---

### Post by panderohit on 2011-02-11
Hi everyone. Great suggestions, thank u. And yes, I detest windows and it pains me when I use it. I wish to get rid of it once and for all. 

Cheers. :)

---

### Post by pricetech on 2011-02-11
The disk you list looks like an install disk, so it should work.

You probably will be prompted to activate windows after you install in VirtualBox, but you can use the number from the COA label attached to your laptop to activate.

---

### Post by panderohit on 2011-02-24
> **pricetech said:**
> The disk you list looks like an install disk, so it should work.

You probably will be prompted to activate windows after you install in VirtualBox, but you can use the number from the COA label attached to your laptop to activate.

  Hi. Yes, that was the Installation disk indeed and it all went through smoothly. :) Thanks a lot for your help, everyone.

---

### Post by Animal X on 2011-02-24
shame you couldn't just dual boot, then you wouldn't have needed v-box.

---

### Post by panderohit on 2011-02-24
> **Animal X said:**
> shame you couldn't just dual boot, then you wouldn't have needed v-box.

I could but I didn't want to. I have dual boot on my desktop already and Windows is used exclusively for iTunes. If I can make iTunes work in Ubuntu in a Virtualbox then that'd be great, else I don't really care, even if my desktop breaks down.  Cheers. :)


**Update**: iTunes works great on the Windows 7 Virtualbox and my iPod syncs *perfectly*. The Guest Additions are a killer. Yay! Take that Bill Gates and Steve Jobs! I'm never coming back to you guys. Bye! Bye!

---

### Post by tomdkat on 2011-03-30
Thanks for starting this thread!  I'm in a similar boat and this info should be VERY useful!  :)

Thanks!

Peace...

---

