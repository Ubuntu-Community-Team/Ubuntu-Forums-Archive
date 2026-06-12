---
title: "Can't detect USB"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by Pysik on 2009-08-31
Hi, I'm pretty new to Ubuntu and so far have found the OS pretty amazing. However I have ran into one problem, and after a few hours searching Google I haven't been able to resolve it.

I can't get Ubuntu to see any of my USB drives, which include my keyboard, mouse, Pendrive and Ext HDD.

I'm not sure what motherboard I have, or how to check that either...

Cheers for any help.

---

### Post by LewRockwell on 2009-08-31
who put that machine together?

.

---

### Post by Pysik on 2009-08-31
I did, but three years ago, I could look inside it to see, but isn't there a way of ubuntu to check it?

---

### Post by LewRockwell on 2009-08-31
[http://ubuntuforums.org/showthread.php?t=634729](http://ubuntuforums.org/showthread.php?t=634729)

footnote: this was found instantaneously via a google search containing the following three words:

ubuntuforums   identifying   motherboard

.

---

### Post by Pysik on 2009-08-31
Thanks for that, that wasn't my main issue though, as, as far as I'm aware I have the correct driver installed out of the box, my usb is just not detected. cheers

---

### Post by LewRockwell on 2009-08-31
> **Pysik said:**
> Thanks for that, that wasn't my main issue though, as, as far as I'm aware I have the correct driver installed out of the box, my usb is just not detected.

the main issue is that those you are seeking assistance from...require information regarding your hardware...not to mention we still don't know which version of Ubuntu you are attempting to utilize

from your original trouble-call posting we read that you have no operational input devices(keyboard/mouse/etc) during your attempts at operating your system with Ubuntu

for more specific guidance regarding the physical hardware you have there then those wishing to provide assistance might well wish to know the operating system you are currently accessing this hardware with(as well as any additional input devices that you currently find operational)

.

---

### Post by Pysik on 2009-08-31
Sorry for any confusion.  I'm trying to access my USB pendrive currently, which doesn't show up. I am using the computer with ubuntu, with non-usb keyboard and mouse connected. And I am on Jaunty Jackalope. 


Result from: 
sudo dmidecode | more
Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
    Vendor: Phoenix Technologies, LTD
    Version: 6.00 PG
    Release Date: 07/28/2005
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 512 kB
    Characteristics:
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported


I hope this information is more useful.

---

### Post by LewRockwell on 2009-08-31
some of those older motherboards had strange and quirky BIOS configurations

not to mention physical jumpers located on the board itself(which might require confirmation of their functioning and current jumping selection)

is legacy USB support one of the selections available in your current BIOS version, and if so...which selection is currently enabled?

you might check this thread out:

[http://ubuntuforums.org/showthread.php?t=1242041](http://ubuntuforums.org/showthread.php?t=1242041)

.

---

### Post by cmannnn on 2009-08-31
it say that your bios is upgradeable i have a similar proble but not my usb it was my sd ports but upraging my bois fixed that

---

### Post by Pysik on 2009-08-31
"sudo lsusb" 

returns nothing. As far as jumper are concerned I'm fairly sure there aren't any, although I will check after posting this. In addition both XP and Mandriva (spring 2007) were working fine for usb support. I'm gonna try upgrading the bios if you think thats a plan.

---

### Post by LewRockwell on 2009-08-31
> **Pysik said:**
> "sudo lsusb" 

returns nothing. As far as jumper are concerned I'm fairly sure there aren't any, although I will check after posting this. **_*In addition both XP and Mandriva (spring 2007) were working fine for usb support**_*. I'm gonna try upgrading the bios if you think thats a plan.

well...see...

now you're giving us additional information that we didn't have knowledge of...in your original trouble-call post...

are you attempting these functions from the LiveCD or a complete and successful full installation of Jaunty Jackalope?

.

---

### Post by Pysik on 2009-08-31
This is a full install, its been running for about three days. XP was running previously on the machine, but hadn't been used for about 6months untill I decided to try ubuntu on here.

Mandriva was also a full install, but that was back in 2007.

---

### Post by LewRockwell on 2009-08-31
do you have USB support when you are running the LiveCD?

we've experienced dozens of *nix distros and USB support has been very solid across a wide variety of platforms so your trouble-call is strange in that regard

.

---

### Post by Pysik on 2009-08-31
Just tried the LiveCD, and no, no USB support either, I agree with you it is very strange... I have to go to work now unfortunately and have another look at this later on.. Thank you for all your help

---

### Post by LewRockwell on 2009-08-31
you might sort out which version of Ubuntu 9.04 Jaunty Jackalope you downloaded and burnt to LiveCD...

32 bit

or

64 bit

.

---

### Post by Pysik on 2009-08-31
Its the 32bit version I'm using.. but its a fully installed version.. also I've remembered that I was using the usb keyboard when I was installing 9.04 so usb was supported on the bios

---

### Post by Pysik on 2009-09-03
Hi. I was just wondering if anyone could offer me some advice on solving this problem?

I can't use any of my USB devices, as ubuntu does not detect them. I can confirm that previously XP had the USB devices, and I installed ubuntu using a USB keyboard (so bios was detecting USB).

I am on Ubuntu 9.04.

Motherboard:

Vendor: Phoenix Technologies, LTD
    Version: 6.00 PG
    Release Date: 07/28/2005
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 512 kB
    Characteristics:
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported

'lsusb' does not show any USB devices. 

Cheers for any help here.

---

