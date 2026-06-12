---
title: "dual boot linux and windows help"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by magedsoft on 2010-08-19
hay all :
  on my uncle's computer windows os ,and i need to install ubuntu 10.04 and i want make dual boot between linux and windows , in past i remmeber when i install linux after windows the computer boot from linux and ignore windows , how can i install ubuntu after windows and when i open the computer i found boot from windows and linux 


thank u i'm waiting >>>>>>>>>>>>>>>

---

### Post by candtalan on 2010-08-19
> **magedsoft said:**
> hay all :
  on my uncle's computer windows os ,and i need to install ubuntu 10.04 and i want make dual boot between linux and windows , in past i remmeber when i install linux after windows the computer boot from linux and ignore windows , how can i install ubuntu after windows and when i open the computer i found boot from windows and linux 
thank u i'm waiting >>>>>>>>>>>>>>>

Hi and Welcome!
Use a Ubuntu Live CD (desktop) version, 10.04.1 which is the latest version.
First use it as a live CD. This is good to check that the hardware runs ok with Ubuntu, audio, sound, display, whatever.

Which Windows do you have on the computer?

---

### Post by wilee-nilee on 2010-08-19
The older boot loader grub-legacy needed editing at times yes.

Grub2 which is part of the install from Karmic and beyond, and is much better at picking up another OS. You can upgrade to grub2 with earlier releases then Karmic, you just want to check the support time.

---

### Post by ranch hand on 2010-08-19
There should, as wilee-nilee says, be no problem.

You may not get the MS OS in the menu when you first boot to Ubuntu.  You may need to open the terminal and run;
```

sudo update-grub

```
and then;
```

sudo grub-mkconfig

```
That last command will give you the contents of /boot/grub/grub.cfg, which is where your screen menu comes from, so that you can check and see if the MS entry is there.

It is also a good idea to use the "advanced" button on the installer screen where you OK installation.  That button just lets you set where grub is installed.  It just wants to be installed on the drive, not on any partitions.

That is > sda  NOT sda1.

Doing that will also make it a lot more likely that MS will be picked up on the update-grub scan that the installer runs so that you have no trouble at all.

There is/was (not sure it was fixed, I do not run MS) a bug where the installer installed grub on the boot sector of MS.  This is not a good thing at all if you want to boot to MS.  Using that advanced button will insure that it will be installed just to the MBR where it belongs.

---

