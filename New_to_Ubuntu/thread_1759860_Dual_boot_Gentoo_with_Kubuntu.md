---
title: "Dual boot Gentoo with Kubuntu"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2011-05-16
I have installed kubuntu on my system and I am planning to install Gentoo! My question how to dual boot Kubuntu and Gentoo using single GRUB menu?

---

### Post by coffeecat on 2011-05-16
It's been a while and bit since I used Gentoo but this is what I would do. I presume you'll be following the [Gentoo Handbook]("http://www.gentoo.org/doc/en/handbook/") for installing Gentoo. If so, do all the steps up to and including 9 - Installing Necessary System Tools. The next step is 10 - Configuring the bootloader. Gentoo still uses legacy grub, so you have three choices:

1 - Follow step 10, emerge grub and include an entry for Kubuntu in your Gentoo grub.conf file, and then continue to 10d - rebooting the system. (Note for others wanting to "correct" my mention of grub.conf. Gentoo uses grub.conf, not menu.lst in its legacy grub.)

2 - Omit installing grub or lilo entirely. Instead, shut down Gentoo and reboot into Kubuntu. Then, from the Kubuntu terminal:

```
sudo update-grub
```...which will put a Gentoo entry in your Kubuntu grub menu.

3 - At step 10, emerge grub in case you want to play with it later but omit the 'grub-install --no-floppy /dev/sda' command at Code Listing 2.6. Then reboot into Kubuntu and run 'sudo update-grub' as above.

**EDIT**: forgot to mention. Have - ah, um - fun when installing Gentoo! :-s

:wink:

---

### Post by 1991sudarshan on 2011-05-16
> **coffeecat said:**
> It's been a while and bit since I used Gentoo but this is what I would do. I presume you'll be following the [Gentoo Handbook]("http://www.gentoo.org/doc/en/handbook/") for installing Gentoo. If so, do all the steps up to and including 9 - Installing Necessary System Tools. The next step is 10 - Configuring the bootloader. Gentoo still uses legacy grub, so you have three choices:

1 - Follow step 10, emerge grub and include an entry for Kubuntu in your Gentoo grub.conf file, and then continue to 10d - rebooting the system. (Note for others wanting to "correct" my mention of grub.conf. Gentoo uses grub.conf, not menu.lst in its legacy grub.)

2 - Omit installing grub or lilo entirely. Instead, shut down Gentoo and reboot into Kubuntu. Then, from the Kubuntu terminal:

```
sudo update-grub
```...which will put a Gentoo entry in your Kubuntu grub menu.

3 - At step 10, emerge grub in case you want to play with it later but omit the 'grub-install --no-floppy /dev/sda' command at Code Listing 2.6. Then reboot into Kubuntu and run 'sudo update-grub' as above.

**EDIT**: forgot to mention. Have - ah, um - fun when installing Gentoo! :-s


:wink:


Is it possible to install gentoo with installing the boot loader like the option we have in the kubuntu installation?

---

### Post by coffeecat on 2011-05-16
> **1991sudarshan said:**
> Is it possible to install gentoo with installing the boot loader like the option we have in the kubuntu installation?

I don't follow you. What option is that?

---

### Post by 1991sudarshan on 2011-05-16
> **coffeecat said:**
> I don't follow you. What option is that?


there is an option called install without bootlaoder! That option comes after the partition table

---

### Post by compmodder26 on 2011-05-16
> **1991sudarshan said:**
> there is an option called install without bootlaoder! That option comes after the partition table

That was what he was referring to in option 2.

> 2 - Omit installing grub or lilo entirely. Instead, shut down Gentoo and reboot into Kubuntu. Then, from the Kubuntu terminal:

```
sudo update-grub
```...which will put a Gentoo entry in your Kubuntu grub menu.

---

### Post by 1991sudarshan on 2011-05-16
> **compmodder26 said:**
> That was what he was referring to in option 2.

so what shall i do?

first :: kubuntu installation without boot loader
next:: gentoo installation with boot loader


or

gentoo installation with out boot loader followed by kubuntu installation with boot loader 



???

---

### Post by 1991sudarshan on 2011-05-16
which file system shall i use for gentoo and kubuntu? ext3 or ext4?

---

### Post by compmodder26 on 2011-05-16
It really shouldn't matter.  Just note that if you do the Gentoo install first without the boot loader, then you will not be able to boot into it until after you install Kubuntu and it detects the Gentoo install and adds it to Grub.

BTW, I think this is a typo, but I want to clarify:
> first :: kubuntu installation without boot loader
next:: gentoo installation without boot loader

You'll want a boot loader installed for one of these.  If you don't do a boot loader for either, then you won't be able to boot either.

---

### Post by kaldor on 2011-05-16
> **1991sudarshan said:**
> which file system shall i use for gentoo and kubuntu? ext3 or ext4?

I'd go with Ext4, since it's newer and apparently faster. That said, I don't notice the difference ;)

---

### Post by compmodder26 on 2011-05-16
> **1991sudarshan said:**
> which file system shall i use for gentoo and kubuntu? ext3 or ext4?

Really a matter of preference.  ext4 is becoming the de facto standard these days.

---

### Post by 1991sudarshan on 2011-05-16
> **compmodder26 said:**
> It really shouldn't matter.  Just note that if you do the Gentoo install first without the boot loader, then you will not be able to boot into it until after you install Kubuntu and it detects the Gentoo install and adds it to Grub.

BTW, I think this is a typo, but I want to clarify:


You'll want a boot loader installed for one of these.  If you don't do a boot loader for either, then you won't be able to boot either.

Thanks for the correction! I will first install gentoo without boot loader followed by the installation of kubunt with boot loader!

---

### Post by coffeecat on 2011-05-16
> **1991sudarshan said:**
> I have installed kubuntu on my system

> **1991sudarshan said:**
> I will first install gentoo without boot loader followed by the installation of kubunt with boot loader!

A bit of a mixup with past and future tenses. I thought you had already installed Kubuntu. :)

Your final choice is as good as any. Just a couple of thoughts. Using the Kubuntu grub bootloader makes it (relatively) easy. Using the Gentoo legacy grub bootloader means you have to learn how to configure it through editing its grub.conf. Good luck with Gentoo. You'll have many frustrating moments but will learn a lot.

---

