---
title: "Using Windows virtually"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by newport_j on 2010-04-19
The powers that be where I work stated that as of May 15, 2010 they will no longer allow dual boot computers. At present my computer is dual boot. The two OS's are Linux and Windows.

I have elected to stay with Linux so I must do something with Windows. I have been told that I can access it virtually using a Linux window. Is this possible? What are the instructions to do it? Where are the instructions to do it. 

What performance hit will I suffer if I do it?

Newport_j

---

### Post by Silent Warrior on 2010-04-19
There are a few virtualization options - VirtualBox, KVM (and QEMU?) - that should do what you're asking for. The catch is that it will need a fair bit of your system RAM; I think this is the biggest performance hit. Also, getting 3D in the virtual machine isn't the least bit straight-forward (in my experience (VirtualBox only), it either works right away, or it never will). If it's just a few isolated apps you need, maybe you should see if they run directly in Linux using Wine.

---

### Post by e4uforums on 2010-04-19
I have XP and Win 7 running in virtual machines with VirtualBox and VMWare - all running just fine.  There is a performance hit if you don't have enough RAM in your machine.  You want to be sure you have enough for Linux, and another 512-1024MB RAM depending on the apps you'll be running in Windows.

To better help you out:

What version of Windows will you run?
What applications will you be running in Windows?
What applications will you be running in Linux?
What hardware do you have in your computer?  (mainly CPU and RAM)

---

### Post by newport_j on 2010-04-28
Okay, I found the virtual box website so I will use virtual box. It is free, anyway. Now I have a dual boot machine (Linux and Windows) and I want to make a single boot machine with only Linux on it and widdnows running in virtual box. 
 
Does virtual box have instructions to convert from dual boot to single boot Linux with windows running in Virtual box? I do not know how to do this.
 
I have never done this before and I do not want to lose anything in doing it.
 
 
Newport_j

---

### Post by mk1w86 on 2010-04-28
> **newport_j said:**
> Okay, I found the virtual box website so I will use virtual box. It is free, anyway. Now I have a dual boot machine (Linux and Windows) and I want to make a single boot machine with only Linux on it and widdnows running in virtual box. 
 
Does virtual box have instructions to convert from dual boot to single boot Linux with windows running in Virtual box? I do not know how to do this.
 
I have never done this before and I do not want to lose anything in doing it.
 
 
Newport_j

Just to check, have you got Windows working in VirtualBox and does it do everything you want it to and perform acceptably etc.?

To remove Windows from your machine you will have to delete the Windows partition first, you can use Gparted on the Ubuntu LiveCD for this.  You can then either expand your Ubuntu partition to fill the space or you can create another partition in its place that you can use for data storage.  Remember to backup any important data before making any changes to partitions!

Once you have removed Windows from your system there will still be a Grub boot entry for it.  How you remove this depends which Ubuntu version you are using.  If you are using Ubuntu 9.04 or earlier or you are using 9.10 and have upgrade from 9.04 you will be using Grub-legacy and will have to remove the Windows boot entry from your /boot/grub/menu.lst file.  If you are using a fresh install of Ubuntu 9.10 or Lucid Lynx you will be using Grub2 and you should be able to remove your Windows boot entry by running:

```
sudo update-grub
```

There is more Grub-legacy information here:

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

and there is more Grub2 information here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by sadaruwan12 on 2010-04-28
Use Virtual Box it's easy and less worrying. Before you do any thing back up your data on to a DVD or to a external storage device.

My opinion to you is do a clean install of your Linux system them install VirtualBox and run WinXP in there. Less trouble :-)

---

### Post by mk1w86 on 2010-04-28
> **sadaruwan12 said:**
> My opinion to you is do a clean install of your Linux system them install VirtualBox and run WinXP in there. Less trouble :-)

I would also recommend this if you don't mind doing a fresh install of Ubuntu, especially since Lucid will be released tomorrow which is a LTS release so you will have three years support instead of the usual 18 months which might be more suitable for a work machine. ;)

---

