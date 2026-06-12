---
title: "Can't get bcm4238 to work,"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by SnackMasterX on 2007-11-18
I've got a Compaq V6500Z laptop with a Broadcom wireless adapter in it. lspci reports it as a BCM4328, but Windows Vista, XP and the HP website call it a BCM4321. I've installed the bcm43xx-fwcutter utility, which seems to have properly installed the firmware, but there doesn't seem to be an eth device detected when I modprobe bcm43xx. There are no errors in dmesg or /var/log/messages. Does anyone else know why it might not be detecting my card?

---

### Post by kevdog on 2007-11-18
Directly from the bcm43xx website the list of support devices:

supported

    * bcm4303 (802.11b-only chips)
    * bcm4306
    * bcm4311 rev 1 / bcm4312
    * bcm4318

Since you have a 4328 or 4321 (doesnt matter since neither is in the supported list), you need to use ndiswrapper -- Sorry -- but ndiswrapper is better anyways -- just more difficult to setup.

---

### Post by SnackMasterX on 2007-11-18
Ok, I've installed ndiswrapper and removed the bcm43xx dirver. Here's the output in dmesg when i try to modprobe ndiswrapper

[  788.006901] ndiswrapper version 1.45 loaded (smp=yes)
[  788.028424] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[  788.030054] ndiswrapper: driver bcmwl5 (Broadcom,06/25/2006, 4.80.28.7) loaded
[  788.030276] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 19 (level, low) -> IRQ 19
[  788.030308] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  788.035013] ndiswrapper (NdisWriteErrorLogEntry:192): log: C000138D, count: 1, return_address: ffffffff88a7264e
[  788.035018] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x10b
[  788.035028] ndiswrapper (mp_init:263): couldn't initialize device: C0000001
[  788.035033] ndiswrapper (pnp_start_device:440): Windows driver couldn't initialize the device (C0000001)
[  788.035043] ndiswrapper (mp_halt:305): device ffff81004032f780 is not initialized - not halting
[  788.035050] ndiswrapper: device eth%d removed
[  788.035056] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[  788.035066] ndiswrapper: probe of 0000:03:00.0 failed with error -22
[  788.040274] usbcore: registered new interface driver ndiswrapper

---

### Post by kevdog on 2007-11-18
Didnt quite get the output!

---

### Post by SnackMasterX on 2007-11-18
Sorry about that, getting ahead of myself with posting reply's here. I corrected my previous post.

---

### Post by kevdog on 2007-11-18
Although there are some bad messages in the output, please post:

lshw -C network

---

### Post by SnackMasterX on 2007-11-18
*-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0

---

### Post by kevdog on 2007-11-18
Do you have another windows xp driver you could try??

Could you also post
ndiswrapper -l

---

### Post by SnackMasterX on 2007-11-18
bcmwl5 : driver installed
        device (14E4:4328) present

---

### Post by kevdog on 2007-11-18
Reboot and then try to modprobe ndiswrapper again. Im kind of stumped!!

---

### Post by SnackMasterX on 2007-11-18
I didn't get to reboot yet because I wanted to try one more thing so I found a new 64-bit driver and decided just to try out the BCM4328 drivers and now the wireless is working so microsoft strikes again, not sure why a different wireless card model driver is necessary under windows but this makes me doubt that OS even more. Thanks for the help though, I can't find the link I used unfortunately however if anyone needs the drivers please PM me your email and I can send them to you.

---

### Post by kevdog on 2007-11-18
The drivers work under ubuntu or windows???

I think bcmwl5 is a 32 bit driver.  I didnt know you were using 64 bit Ubuntu.

---

### Post by SnackMasterX on 2007-11-18
Found the link, [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") and things seem to be working great now, I am running off of wireless as well through WPA. Thanks for the assistance!

---

### Post by SnackMasterX on 2007-11-18
Sorry, I thought I mentioned that in the original post, I have to use a completely different driver though under ubuntu than windows. I use the BCM4321 under windows but need the BCM4328 under ubuntu.

---

### Post by kevdog on 2007-11-18
Thanks for the update -- so the wrong windows driver strikes again!!!

---

