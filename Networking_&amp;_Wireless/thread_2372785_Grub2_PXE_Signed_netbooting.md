---
title: "Grub2 PXE Signed netbooting"
date: 2017-09-28
forum: Networking &amp; Wireless
---

### Post by gizmoshq on 2017-09-28
OK, I am a very seasoned PXE Deployment person, who currently is being pushed into secure boot.  

My current environment has a series of tools launched via PXE to service a number of machines.  It is not practical to put them on a stick.  It is not practical to disable Secure Boot.  It is not practical to use PXE Linux, as we need Secure Boot and PXE Linux doesn't compile without a lot of work on any current version of Linux.  

We are currently distributing out custom Windows PE Software wtih Bootmgfw.efi , launched via PXE, and that is great except it won't let us launch non Microsoft goodies, like Memtest86 UEFI, or the new Parted Magic that is Secure Boot supported.   So I am looking at Grub2.  

I am using the Grub2 signed from Ubuntu 14, which will load an unsigned kernel after SHIM loads it. HOWEVER, everhy signed version of Grub2 I load times out when loading the Bootmgfw.efi file.   My setup is as follows:

ISC DHCP Server 4.5x
HPA TFTP Server Latest
Lubuntu Latest as DHCP server. 

Test environement Hyper-V with Microsoft UEFI Secure Boot enabled, and several different brands of laptops.  I am able to reproduce the problem without Secure Boot enabled as well, so we don't have to bark up that tree.  

No matter what I do, here is my output from Grub.  I have loaded all modules, and even loaded from the command line of Grub itself, and attached a screenshot.   

TFTP Server shows a connection starts and then stops.  Done with TFTPD32 and HaneWin DHCP.  Problem is only with Grub, I have booted the crap out of everything with Bootmgfw and PXELINUX,but good ol Pxelinux is depreciated.

---

