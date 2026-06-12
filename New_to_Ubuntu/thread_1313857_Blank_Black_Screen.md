---
title: "Blank Black Screen"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by owyzzz on 2009-11-04
Hi All,

I have a problem installing Ubuntu 9.10 in my Compaq Presario laptop. These are the specs of my laptop:

------------------
System Information
------------------

Operating System: Windows Vista™ Home Premium (6.0, Build 6002) Service Pack 2 (6002.vistasp2_gdr.090803-2339)
Language: English (Regional Setting: English)
System Manufacturer: Hewlett-Packard
System Model: Compaq Presario CQ61 Notebook PC
BIOS: Default System BIOS
Processor: Genuine Intel(R) CPU T1600 @ 1.66GHz (2 CPUs), ~1.7GHz
Memory: 1978MB RAM
Page File: 1476MB used, 2723MB available
Windows Dir: C:\Windows
DirectX Version: DirectX 10
DX Setup Parameters: Not found
DxDiag Version: 6.00.6001.18000 32bit Unicode


---------------
Display Devices
---------------
Card name: Mobile Intel(R) 4 Series Express Chipset Family
Manufacturer: Intel Corporation
Chip type: Mobile Intel(R) 4 Series Express Chipset Family
DAC type: Internal
Device Key: Enum\PCI\VEN_8086&DEV_2A42&SUBSYS_3069103C&REV_07
Display Memory: 797 MB


I'm planning a dual boot OS for my laptop. I have already parted a space (40GB) for Ubuntu using Windows Vista. Then I downloaded the latest version of Ubuntu (filename-ubuntu-9.10-desktop-i386) and then burned it on a cd. My first problem has something to do with burning the cd, but I found that the solution that is to burn at the slowest possible burning speed. So starting up, I changed the priority level of disc devices in BIOS. It set the CD-ROM at the top of the list. Then came the Ubuntu cd menu. Here's the problem:

a.) I first chose "Try Ubuntu with out changes..." just to try and see it and then, the screen went plain black. I waited for 30 minutes and still nothing happened.

b.) I then tried to choose "Install" then the screen again went black. It didn't install--think there was an error message.

c.) Now I tried using WUBI and it did install. And so after installing, and rebooting, came the boot OS menu, I chose Ubuntu but the screen went black. I waited for 20 minutes and it rebooted on its own. Came again the boot OS menu, I chose Ubuntu again and the screen went black again. I waited for another 20 minutes and nothing happened.

d.) Now I formatted the Ubuntu partition and downloaded the former version 9.04 (ubuntu-9.04-desktop-i386), then burned in a cd. And did the same thing again. Then I reformatted again and downloaded the WUPI for 9.04 and successfully installed, but the screen went black again after choosing Ubuntu in the boot OS menu. What happened was just like in a.) b.) and c.)

e.) Just this morning, I found out about the alternate installer. I downloaded it (karmic-alternate-i386) and burned in a CD (because it cannot be installed using WUPI, correct me if I'm wrong) and installed. After placing all the needed info in the fields, it was successfully installed. It then rebooted, and then I choose again Ubuntu in the boot OS menu (GRUB) and the screen went black again..

I'm really tired and stuck at this moment trying to install this OS. I really wanted to use this though since it was recommended to me by a colleague. Anybody knows how to solve this?

Regards,

Jan

---

### Post by iMisspell on 2009-11-04
I had a simulare problem and it was video driver related, heres how i installed.

Popped in cd, got to main options/install screen...
Cursored down to 'Install'.
Pressed F4 and selected "Safe graphics mode"
and installed.

AThe install when smooth and after i got to the Ubuntu desktop i had to install video drivers (for me it was a desktop machine ATI HD3850 vid-card).

But the F4 "Safe graphics" worked for me, no more black screens and it installed fine.

Im new to linux and ubuntu, so that is just my experience, not saying it will help you.

Good luck.

_

---

