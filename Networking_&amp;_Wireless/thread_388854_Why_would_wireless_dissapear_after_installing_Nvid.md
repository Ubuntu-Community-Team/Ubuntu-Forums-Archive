---
title: "Why would wireless dissapear after installing Nvidia drivers? 3945"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by Jamshedk on 2007-03-20
I have tried this a hundred different ways and every time I install Nvidia drivers my wireless Intel 3945 ABG card disappears when I reboot.

If I use ENVY or just follow nvidias instruction line by line.  

What possible connection could they have?  I actually reinstalled ubuntu just to make sure... and yup it happened again...

Are there other users that are experiencing this? or only 3945 users?

---

### Post by Jamshedk on 2007-03-20
also I ran this command and it seems like it should work

[PHP]slim@slim-laptop:~$ lsmod | grep ipw
ipw3945               124576  0 
ieee80211              35272  1 ipw3945
slim@slim-laptop:~$ 

[/PHP]

I ran 
[PHP]sudo modprobe ipw3945[/PHP]

and went back to System Administraot Networking and still only my wired connection shows up...



ALSO I ran yhtat little dmesg and everything looks ok:

[php][17179602.640000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[17179602.644000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 82
[17179602.644000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179602.652000] Bluetooth: HCI USB driver ver 2.9
[17179602.652000] usbcore: registered new driver hci_usb
[17179602.680000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
[17179602.680000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179602.692000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17179602.692000] sdhci: Copyright(c) Pierre Ossman
[17179602.712000] ts: Compaq touchscreen protocol output
[17179603.396000] sdhci: SDHCI controller found at 0000:08:09.1 [1180:0822] (rev 19)
[17179603.396000] ACPI: PCI Interrupt 0000:08:09.1[B] -> GSI 18 (level, low) -> IRQ 185
[17179603.396000] mmc0: SDHCI at 0xd6101800 irq 185 DMA
[17179603.404000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 19 (level, low) -> IRQ 193
[17179603.404000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[17179603.404000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[17179604.148000] lp: driver loaded but no devices found
[17179604.176000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179604.176000] ieee1394: sbp2: Try serialize_io=0 for better performance
[/php]

---

### Post by Jamshedk on 2007-03-22
I was thinking is there a specific setting that is changd when drivers are install that can reflect any type of impact on network settings mainly wireless?  or what config files does installing nvidia drivers change? other then the xorg.conf?

---

### Post by serafimsaudade on 2007-03-25
i got de same problem, i have install the lasted drivers ou nvidia, anda my wireless stop work. I need help !!!

---

### Post by falcons7 on 2007-03-26
bump.... same problem and same outputs

---

### Post by Jamshedk on 2007-03-27
Serafimsaudade/Falcons, do you guys have the 3945 chipset or do you have a different wireless controller?  

Im at the stage where I think Im going to remove the wireless card install ubuntu, install beryl and nvidia drivers, and then MANUALLY put the wireless card back in and see if that works.. it's just such a pain haha :)

Ill try it this weekend and keep you guys posted...

---

### Post by chili555 on 2007-03-27
I just saw this, which looks promising: [http://www.ubuntuforums.org/showthread.php?t=392265&highlight=ipw3945](http://www.ubuntuforums.org/showthread.php?t=392265&highlight=ipw3945) See post #4.

---

### Post by Jamshedk on 2007-04-04
> **chili555 said:**
> I just saw this, which looks promising: [http://www.ubuntuforums.org/showthread.php?t=392265&highlight=ipw3945](http://www.ubuntuforums.org/showthread.php?t=392265&highlight=ipw3945) See post #4.

Hmm yeah its a partial solution but the poor fellow still has to reinstall the nvidia drivers every single time you boot up which can be very painful on a laptop that is turned on and off 4-5 times a day...

hopefully soembody else will chime in with a solution

---

### Post by Jamshedk on 2007-05-21
anything?

---

