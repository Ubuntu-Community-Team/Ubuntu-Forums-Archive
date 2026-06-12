---
title: "how to auto update boot menu?"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by pft0 on 2010-12-23
i have installed 10.04 on my sdhc card in my mobile broadband modem, and i can boot into ubuntu on almost any machine, but when i want to boot into windows, i need to first login to ubuntu, update the grub menu, then restart, is there any way the boot menu can be updated at boot time?

---

### Post by amjjawad on 2010-12-23
> **pft0 said:**
> i have installed 10.04 on my sdhc card in my mobile broadband modem, and i can boot into ubuntu on almost any machine, but when i want to boot into windows, i need to first login to ubuntu, update the grub menu, then restart, is there any way the boot menu can be updated at boot time?

```
sudo update-grub
```From Terminal.


Edit:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
This link will help you to understand more about GRUB2.

---

### Post by pft0 on 2010-12-23
thanks for the reply, i known update-grub from terminal, but what i would like to ask is there any way to update the boot menu BEFORE grub menu appear(so i don't have to log in to ubuntu before i boot the local OS), not after i have logged in ubuntu

---

### Post by amjjawad on 2010-12-23
> **pft0 said:**
> thanks for the reply, i known update-grub from terminal, but what i would like to ask is there any way to update the boot menu BEFORE grub menu appear(so i don't have to log in to ubuntu before i boot the local OS), not after i have logged in ubuntu

You just need to do grub-update once. After that, every time you boot and your card is plugged in, you'll see the other OS entry in your list.

---

### Post by oldfred on 2010-12-23
If you are using it to boot different systems on different hardware, you can add extra boot stanzas to 40_custom by copying each system's boot stanza from the update grub. 

About the only other choice is to change to manual mode and either edit the boot stanza that exists or totally manually specify partition to chain load and boot. You can use ls to list bootable partitions to help find which may be bootable.

Edit:
Since windows will have to be on one of the primary partitions 4 entires like this will let you boot any primary partition. Just make one for each partition.

# Chainload another bootloader
menuentry "Chainload partition 3" {
set root=(hd0,3)
chainloader +1
}

Not sure if you add the insmod ntfs if then it would recover after an error to an incorrect partition or not.

---

### Post by pft0 on 2011-01-07
the problem i found is that i not only boot into ubuntu or windows, i also have arch linux, novell suse, centos and other os which can be on any partition, so i just though if i can do something like update-grub2 before the boot menu start

---

### Post by amjjawad on 2011-01-07
> **pft0 said:**
> the problem i found is that i not only boot into ubuntu or windows, i also have arch linux, novell suse, centos and other os which can be on any partition, so i just though if i can do something like update-grub2 before the boot menu start

I posted the link for GRUB2 and it's the last one in my signature. Try to read more about GRUB2.

GRUB2 should be able to boot any other system. I had 9 OS's installed on my PC not long time ago and with one command, GRUB2 was able to find all the other systems and I had to do it once only.

```
sudo update-grub

```
is all what you need. 

Everytime you add more OS's, just make sure NOT to install their boot loaders in the MBR and after you're done with their installation, login to Ubuntu and run "update-grub" and it's done.

Edit:
You don't need to run that at boot-time. While you're logged in to Ubuntu, you can run "update-grub" from terminal and that's all. Again, in case you'll add more systems, after each installation, "update-grub" should be run while you're logged in to Ubuntu.

---

### Post by Yougo on 2011-01-07
Isn't the OP specifically asking for alteratives to update-grub? repeating update-grub won't help him

@pft0
am i reading correctly that you have multiple existing systems, and want to plug in an external device with ubuntu loaded on it and then choose to boot either the drive or a natively installed OS?

do you have acces to BIOS boot options? on my machine it's something like ctrl+F12 during BIOS splash, which takes me to a list of available bootable drives.

---

### Post by amjjawad on 2011-01-07
> **Yougo said:**
> Isn't the OP specifically asking for alteratives to update-grub? repeating update-grub won't help him

@pft0
am i reading correctly that you have multiple existing systems, and want to plug in an external device with ubuntu loaded on it and then choose to boot either the drive or a natively installed OS?

do you have acces to BIOS boot options? on my machine it's something like ctrl+F12 during BIOS splash, which takes me to a list of available bootable drives.

I'm offering the "easiest" and the "simplest" way to do that. I don't know any other method. Perhaps oldfred already explained one.

Don't confuse between BIOS, the Priority of each Bootable Device and the Boot Loader (which is GRUB2 in this case).

The OP is using an external device which has Ubuntu.
Usually, in such cases, it's recommended to install GRUB2 in the MBR of that external device. Why? because that device will be bootable anytime anywhere and with single command which has 3 words only, he/she can be able to boot any other systems.

If he'll change the BIOS Boot Sequence then he/she will NOT be able to boot and login to Ubuntu "unless" GRUB2 is installed in the MBR of the internal HDD.

GRUB2 is very flexible but you just need to know how to deal with it.

---

### Post by Yougo on 2011-01-07
i'm not sure i follow

example: 
-i have a pc with, say, XP and SUSE installed, powered off.
-i plug in an external drive with ubuntu installed.
-i swich the pc on, and at BIOS splash i go to the boot selection menu.
  -if I choose USB, it loads ubuntu
  -if i choose HD it proceeds to display SUSE's grub from where i can choose XP or SUSE.

it bypasses any sort of integration of different installs, and allows you to boot ubuntu on any machine. provided you have BIOS access ofcourse

if OP really specifically wants to update grub between switching the computer on and running grub, i don't know how.
it would indeed be sweet if grub could look around and update itself before displaying.

---

### Post by amjjawad on 2011-01-07
> **Yougo said:**
> i'm not sure i follow

example: 
-i have a pc with, say, XP and SUSE installed, powered off.
-i plug in an external drive with ubuntu installed.
-i swich the pc on, and at BIOS splash i go to the boot selection menu.
  -if I choose USB, it loads ubuntu
  -if i choose HD it proceeds to display SUSE's grub from where i can choose XP or SUSE.

it bypasses any sort of integration of different installs, and allows you to boot ubuntu on any machine. provided you have BIOS access ofcourse


Again, you're confusing between BIOS and GRUB2.

There are two kind of sequences/priorities in BIOS:

1- Device Priority [CDROM, HDD, NETWORK, etc]
2- HDD Priority [HDD1, HDD2, HDD-USB, etc]

GRUB2 is a boot loader. 

[http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)


In your example: It's not how you set your Devices "and" your HDD Priority, it's "where" did you install GRUB2 and based on that, you'll change your BIOS Priority. I know it's a bit complicated so I'll explain more.

Before I do that, you need to understand the basics:
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

**>> If you install GRUB2 in the MBR of your USB Flash Drive:**

a)  that USB Flash Drive will be bootable and can be used on any other machine.

b) if your USB Drive is plugged in + BIOS set to boot from USB-Drive as the first "HDD" to boot from then your machine will boot from USB Drive and login to Ubuntu

c) if your USB Drive is NOT plugged in, it doesn't matter what BIOS sequence do you have, your machine will boot (if set) from your HDD and it will boot depending on what is installed there.

**>> If you install GRUB2 in the MBR of your HDD:**

a) your machine will not boot and login to any other OS "unless" your USB Drive is installed. GRUB2 files will be stored in your USB Drive (/boot/grub) so the USB Drive must be plugged in to boot other systems.

b) your USB Drive will NOT be bootable on other machines. The MBR of your USB Drive does not have any information and does not point to your root partition where GRUB2 files are installed.

c) this kind of installation/setup is NOT recommended. I'm not saying it's wrong but I'm saying it's not recommended.


In my signature, there are lots of useful information. Check "Dual-Boot Guide" if you're interested.

> it would indeed be sweet if grub could look around and update itself before displaying.
Perhaps but I do prefer to do it myself.

---

### Post by Yougo on 2011-01-07
i know what grub is and i know hat BIOS is. i'm not confusing them, i'm saying that you can use your BIOS boot options to get to ubuntu on USB or whatever you have on your HD, without tinkering with grub.

the usb drive has its own grub, as it is a self contained install. same with the HD, it too has its own bootloader. they don't know of eachother

sure it'd be nice to have all your OSses listed according to what drives you plugged in or out just prior to booting, but grub just doesn't do that AFAIK.

i'm by no means a programmer, but i suppose some sort of mini-os could be loaded on a small primary partition of the USB which only job it is to mount the USB's ubuntu partition, update its grub to include the HD's OSses and then run grub. 
this would be nice on a live cd too. instead of "boot from your harddrive" it could give you a list of what you have.

---

### Post by amjjawad on 2011-01-07
> **Yougo said:**
> i know what grub is and i know hat BIOS is. i'm not confusing them
I'm sorry if I did not make myself clear but I did not mean you do not know about GRUB2 and BIOS, whenever I post, I include external links for better understanding :) 

> **the usb drive has its own grub, as it is a self contained install. same with the HD, it too has its own bootloader. they don't know of eachother**
I'm afraid we're talking apples and oranges here.

The USB Drive will NOT have it's own boot loader UNLESS you install it yourself. GRUB2 during Ubuntu Installation will be installed "by default" in**[COLOR=Red] /dev/sda[/COLOR]** which means the MBR of the first HDD in your machine.
If you won't change that option in step 8 which is the last step before installation, then your USB Drive will not have its own boot loader (GRBU2), period.
You may be right ONLY if your USB Drive is /dev/sda.

My point is: USB DRIVE will not have its own boot loader UNLESS you choose that during installation.

Same goes for the HDD, it depends on what OS is installed and what boot loader is installed there.

I'm not trying to disagree with you, I'm trying to explain my point and explain the relation between the boot loader and BIOS.

> sure it'd be nice to have all your OSses listed according to what drives you plugged in or out just prior to booting, but grub just doesn't do that AFAIK.
Last step in the installation process, if you notice, the installer will run "update-grub" before the restart.
And as always, you can do it from terminal. I don't know why it's a problem to type 3 words command?

GRUB2 "does" that indeed. Automatically during installation and after that if you added more systems after you have installed Ubuntu.

Again, perhaps it's nice if GRUB2 will auto-update itself but I'm not quite sure how good/bad that would be.

---

### Post by Yougo on 2011-01-07
well if the OP wants to take the usb and plug it in wherever he likes, it'd better have its own grub or some sort of bootloader or it won't boot.

no, sudo update-grub is not hard to type. but that's not the point. 

booting into ubuntu, logging in, launching a terminal, type sudo update-grub, reboot, hold shift key, and select windows, just to boot windows every time gets tedious i imagine.

---

### Post by amjjawad on 2011-01-07
> **Yougo said:**
> well if the OP wants to take the usb and plug it in wherever he likes,** it'd better have its own grub or some sort of bootloader or it won't boot.** 
That is exactly what I've been trying to explain since the beginning :)

> 
no, sudo update-grub is not hard to type. but that's not the point. 

booting into ubuntu, logging in, launching a terminal, type sudo update-grub, reboot, hold shift key, and select windows, just to boot windows every time gets tedious i imagine.I agree it's a bit of a headache to do that every time but note that you need to do this ONLY IF you want GRUB2 which has been installed in the MBR of the USB Drive (to make it bootable every where) to boot OTHER OS's installed on OTHER Machines.

Otherwise, if you're going to use this USB Drive on your machine where you first installed Ubuntu on your USB Drive, then you DO NOT need to do that at all "unless" you have installed another system after Ubuntu.

Also, you do NOT need to do "grub-update" even when you plug that USB Drive into other machine UNLESS you want to select all the OS's installed on the other machines.

If the main purpose of that USB Drive is to boot Ubuntu and login to it, then no "update-grub" is required whatsoever.

It's required only when ... well, I already explained that ;)

---

### Post by Yougo on 2011-01-07
gong from the OP's intention to use the device on multiple machines i assumed the device had its own grub. he'd need to update everytime he switches system.
it'd be required fairly often.

...unless you use the BIOS

---

