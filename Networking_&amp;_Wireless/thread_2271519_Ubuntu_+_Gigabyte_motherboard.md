---
title: "Ubuntu + Gigabyte motherboard"
date: 2015-03-30
forum: Networking &amp; Wireless
---

### Post by andy133 on 2015-03-30
Greetings All,

Following prompts from peers I am taking the plunge to use/learn/deploy Ubuntu for myself and clients. Hoorah.

I am planning a PC build and my candidate motherboard is the Gigabyte GA-H97N-Wifi motherboard due to its built in wifi/BT adapter.

My first question, and the big one, does anyone have any experience combining Ubuntu with this motherboard, positive or negative. If I can quickly avoid any issues or show stoppers I would like to do so.

Second, if this is not (yet) answerable, when I install the OS, can someone point me to where I can determine if the WiFi functionality has been recognized?

Obviously a newbie question, but the journey must begin somewhere.

A.

---

### Post by kurt18947 on 2015-03-30
I don't have that MoBo, my newest is an AMD a couple years old. Do you know the chipset of the WiFi/BT adapter? I did see mention of Atheros though no specifics. IME Atheros support is pretty good. If the chipset is supported, your life might be pretty simple. If it's a new/unsupported chipset, you life might get pretty complicated :). One big difference between Windows and Linux is that many device drivers are part of the kernel. Plug in the hardware or boot the machine and it works, no discs or downloads required. If the chipset is not built into the kernel, you may have to download a binary that supports your hardware or you may have to download the source and compile it or you may be out of luck. This information may not be readily available and components may change during a manufacturing run. 

I'm no pro, just a hobbyist. I try to do my homework before purchasing hardware as you are doing. I've been very fortunate over the years, can't think of a piece of hardware I've had that wouldn't function on Linux. I try to stay a ways back from the bleeding edge. If a device or chipset has been around for a year or more, the liklihood of its being supported is pretty high.

---

### Post by oldfred on 2015-03-30
Across several models with both Intel & AMD, Gigabyte has issues with an IOMMU setting in UEFI. Once that is resolved it seems to work.
A few have called for support from Gigabyte and they specially say they do not support Linux. But many vendors have similar policies for first level help desk staff.

 Gigabytes P67 & H67 hybrid efi -Hybrid EFI is a UEFI based on the open source TianoCore
[http://www](http://www).[rod]("http://www.rodsbooks.com/gb-hybrid-efi/")sbooks.com/gb-hybrid-efi/
[http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html](http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html)
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)



I just built a system with Asus-AR and had a lot of issues getting all the settings correct, so it would boot in UEFI mode. But been working fine since.

You should plan on UEFI with gpt partitioning. If not familar there are many of the standard better links in the link in my signature below.

---

### Post by andy133 on 2015-03-30
Thanks guys. I have some reading to do now obviously. Probably a good way to learn Ubuntu.
Im hopeful that it works out of the box of course.

A.

---

### Post by kurt18947 on 2015-03-31
This is purely speculation on my part. I have an older Gigabyte MoBo - GA-MA785GM-US2H - that boots live USBs that have been formatted to FAT32 with DOS or Windows just fine. If I format a USB using Gparted then install a live install, that USB will not boot, it gives an error. The same drive when plugged into several Thinkpads or a current Asrock MoBo with a UEFI hybrid BIOS boot just fine. In researching the problem, I read somewhere on the internet (so it must be true!:p) that the boot portion of the modular BIOS was written by Microsoft. Makes me wonder if Gigabyte is trending toward "we only care about booting easily with Windows. If you can get our products to work with other OS s good for you but we're not helping".

---

