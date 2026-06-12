---
title: "need help, I/O resource piix4_smbus conflicts with ACPI region SM00"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by ibz41 on 2009-11-06
Please help, I recently installed ubuntu 9.10 32 bit and I am having issues booting. I tried using regular install method which I could not get to install properly. I then used alternate install method and made it through full installation. The first time I tried to boot the computer the ubuntu symbol came up for a moment and then screen went blank. I rebooted, waited for ubuntu symbol to appear and hit esc. Then i saw a message at the top of the screen "**general error mounting filesystems. A maintenance shell will now be started. CONTROL-D will terminate this shell and re-try. ****root@ubuntu****~# [9.887464] ACPI: I/O resource piix4_smbus [0xb00=0xb07] conflicts with ACPI regionSM00 [0xb00-0xb07]"**

---

### Post by tgalati4 on 2009-11-06
Is this seriously old hardware?

---

### Post by ibz41 on 2009-11-06
trying to install on a compaq sr1730z, amd athlon64x2 2.2ghz, 1 gig ram, about 2 1/2 yrs old

---

### Post by lovekid on 2009-11-19
I think you can try AMD 64bit.

The AMD motherboard must has something different for intel, especially the ACPI. In china, i saw a motherboard made by &#21326;&#30805;, which support AMD,has an especial ACPI, no matter how hard i work, it won`t work, at last i install amd 64bit

but if disable acpi, it can work, you can google how to disable acpi, it seems configure the grub menu.lst

i am so sorry my english is poor

---

