---
title: "System Incompatibility??"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by rosehipzero on 2010-05-16
THANKS EVERYONE! It took some advice and playing around to get it through. I had to use pci=nomsi as well as ACPI Workaround to make it work. Thanks guys! :3

OK! First off, hello Ubuntu! I've been using (and playing) with different Linux distros for over a year now (quite fun ^^)!!! And the new Lucid drew me back to Ubuntu from Jolicloud and Linux Mint, great great great release!!!

OK! Now to be serious. After Christmas rolled through, i bought a new MoBo. I bought a XFX nForce 750a replacing my terrible cheapy MSI (crashed and thrashed ><). However, ever since my hardware update, ALL (and i mean every) Linux distro i've tried, has failed.

I've tried the following:

1. LiveCD's (and LiveDVD's)
2. LiveUSB
3. OEM CD/DVD's (someone suggested it)
4. And also older versions of distros
5. I've been using the AMD64 alternative ISO's

Also, to my surprise, Linux crashes inside Sun VirtualBox too!!!

I've tried the god Google for answers, but nothing pertaining to my issue. 

I've tried Linux Mint, Ubuntu (8,9, and now 10), I've tried ArcLinux... everything yields the same results. No booting, if it boots - it crashes, failed installs, WUBI fails ... the whole lot!

Is it my motherboard?

---

### Post by friv_livs on 2010-05-16
Sounds like your hardware is linux incompatible.

Google "ubuntu wiki", navigate to the hardware compatibility list, and bookmark.

The list is a little out of date testing wise, but it covers most hardware.

---

### Post by Daveth on 2010-05-16
if you are running SATA drives, there appears to be an issue with Linux seeing them.
This

[http://www.bjorn3d.com/forum/showthread.php?t=28461](http://www.bjorn3d.com/forum/showthread.php?t=28461)

suggests a solution to try.

---

### Post by steveneddy on 2010-05-16
I only purchase Linux compatible hardware from vendors who work for the community.

I prefer System76 because I mostly purchase laptops for myself and my daughters. I purchase the latest/greatest  that they offer so that the hardware will be fast enough for a few years and I always feel that I get my money's worth.

This three year old lappie has been through 5 versions of Ubuntu with nary a hiccup or install issue. Not even wireless due to the Intel wireless chip which is well supported under Linux.

The best way to replace hardware is to do your research on the web and on UF and only purchase hardware that works well with Linux.

Sometimes that hardware is a little more expensive, but it's worth it in the end because you aren't beating your head on the desk just trying to get lame hardware to work properly.

My advice would be to do a little research and take the Mobo back and exchange it for a unit that would work better with your OS.

Cheers

---

### Post by rosehipzero on 2010-05-16
Oh thanks for the replies! i'll look into a the SATA drives. I have a 500 GB Western Digital Green Cavier HDD and a Seagate 160GB Barracuda HDD (its only for installing my steam games)

Either of these products might be it... but, i'll go for the install again!!!! thanks guys :3

[EDIT] where do i type "pci=nomsi" for the boot install? when im prompted or some other menu?

---

### Post by rosehipzero on 2010-05-16
I was told that i had a similar problem to one encountered by a helpful ubuntu user, but could not figure out what to do with this code.

I wasnt able to figure out when and where i was to type PCI=NoMSI when trying to install Ubuntu. 

I'm trying to install Ubuntu, but it keeps crashing. The liveCD's crash and i cant continue the Installation from the WUBI install i ran. I'm trying to use the AMD64 alternative of Ubuntu 10.04 for my desktop.

if further info is required, please ask what you would like to see

---

### Post by mikewhatever on 2010-05-17
pci=nomsi looks like a boot option. When booting from the live cd, hit any key right after the BIOS screen. The live session should stop loading and you'll be presented with language selection and some options behind it. Select a language, then hit f6, don't select anything, just hit Esc. Now, there should be a line of text at the bottom, add your boot option to it and hit enter.

---

### Post by cariboo on 2010-05-17
Merged 2 threads on the same subject.

---

### Post by rosehipzero on 2010-05-18
> **mikewhatever said:**
> pci=nomsi looks like a boot option. When booting from the live cd, hit any key right after the BIOS screen. The live session should stop loading and you'll be presented with language selection and some options behind it. Select a language, then hit f6, don't select anything, just hit Esc. Now, there should be a line of text at the bottom, add your boot option to it and hit enter.

OK! thanks! ^^ hopefully this works, i've been dying to use the new ubuntu on my computer. I havent used Ubuntu since Christmas when i bought this MoBo

---

