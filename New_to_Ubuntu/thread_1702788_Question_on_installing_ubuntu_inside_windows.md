---
title: "Question on installing ubuntu inside windows"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by karthik.chopper on 2011-03-08
Hi guys, this might be really silly, i want to know if installing UBUNTU 10.10 using the wubi as "INSTALL INSIDE UBUNTU" option load the windows drivers first before loading ubuntu


[LIST=1]
[*]What is the difference between dual booting and installing inside windows.(i am using windows 7)
[*]I installed it in my desktop as inside windows and i can see the boot load screen showing me both the options but my friend tells me that the windows loads first and then only ubuntu loads. Is this true???
[/LIST]
I use a DELL STUDIO XPS 16. It does not have any windows install discs. Only the recovery discs which i created on loading the laptop for the first time. I dont want to screw up the windows section as sensitive data is present there and one time install aplications are there(one PC licenced ones). So i want to have control over the bootloader with the windows itself and not the GRUB so that i can unistall whenever i want to. I heard you can do it with EasyBCD. If used can you kindly show me the procedure to do the same????

---

### Post by LinuxFox on 2011-03-08
As far as I know, installing inside Windows does not install drivers.  All Wubi does is creates a virtual disk and adds Ubuntu to Windows Boot Loader.  It can be removed via "Add/Remove" in Windows.

As for what you want to do, I'm sorry I have no experience with that.  Though Wubi uses Windows Boot Loader.  You choose using Windows Boot Loader.  There will be GRUB after choosing Ubuntu, but it's part of Wubi and does not interfere with Window's Boot Loader.

Hope this information is useful.  I'm currently using a regular dual-boot on my laptop, but I use to use a Wubi install.  From my experience, they both run the same, except you can't hibernate with Wubi.

Just to be on the safe side, if you don't want to ruin your sensitive data, try backing up files.  Whether it's a CD or DVD, a flash disk, or even an audio player or iPod (some models have an "Enable Disk Use" option).  Backing up is a good habit to have.  Can't do this with installed software, but you can with documents and such.

---

### Post by jerome1232 on 2011-03-08
They only difference between wubi and a real install, is that your using a giant file on the windows drive as a virtual disk, and you are using the Windows boot loader.


So you get two layers to your filesystem (you are writing to a file formated as ext4 which is on a nt filesystem) which can slow down disk operations.

Other than that wubi is exactly like a regular old install. It doesn't inherit drivers from Windows or anything fancy.

edit: All things wubi can be found here: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)


Take a look around I'm sure it has something about the bootloader.

---

### Post by karthik.chopper on 2011-03-08
Hey, thanks for the immediate reply. Let me phrase my query this way, does installing inside windows load windows and then load ubuntu???? that is, it loads windows totally or partially and then only boot ubuntu when i select ubuntu from the boot screen??

Or it directly boots Ubuntu and not boot/load windows when selected.

---

### Post by Rubi1200 on 2011-03-08
Wubi adds an entry to the Windows bootloader. It is Windows that controls the boot process.

When you start the computer you will see a menu with the choice to boot either operating system.

If you decide to remove Wubi, you will be back to the familiar Windows boot splash screen.

---

### Post by LinuxFox on 2011-03-08
> **karthik.chopper said:**
> Hey, thanks for the immediate reply. Let me phrase my query this way, does installing inside windows load windows and then load ubuntu???? that is, it loads windows totally or partially and then only boot ubuntu when i select ubuntu from the boot screen??

Or it directly boots Ubuntu and not boot/load windows when selected.When using Wubi, it loads the Windows Boot Loader and you select from there.  When you choose Ubuntu it will boot Ubuntu.  It's like choosing a different OS when it's installed inside Windows.

To put it best I can, it acts like another OS is installed, except Windows sees it as another program, thus why it can be removed easily via Add/Remove.

Hope this helps. :)

---

### Post by jerome1232 on 2011-03-08
It doesn't load windows at all. Only the boot loader. Once you choose to boot Ubuntu it's all Ubuntu.

---

### Post by Frogs Hair on 2011-03-08
Info:[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

