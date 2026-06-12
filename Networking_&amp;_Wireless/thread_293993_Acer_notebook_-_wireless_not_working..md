---
title: "Acer notebook - wireless not working."
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by 'Orrible Cabbage on 2006-11-06
Hi.  I'm a complete noob to the whole Linux/Ubuntu thing.  I have installed Edgy on an Acer TravelMate 4060 (dual booting with XP), and no matter what I do I cannot connect to my wireless network.

I have installed the correct driver with NdisWrapper, and it tells me the driver is installed and the hardware is working.  I installed network-manager, but it does not offer me any choices for wireless networks.

If anyone can help me or point me in the right direction I'd really appreciate it.  Thanks.

---

### Post by T-Roy on 2006-11-06
try pushin F2 on startup u might have 2 turn it on from there under wireless

---

### Post by 'Orrible Cabbage on 2006-11-06
> **T-Roy said:**
> try pushin F2 on startup u might have 2 turn it on from there under wireless

Do you mean in BIOS? There is no wireless setting in BIOS that I could see.

---

### Post by Xemanth on 2006-11-06
> **'Orrible Cabbage said:**
> Hi.  I'm a complete noob to the whole Linux/Ubuntu thing.  I have installed Edgy on an Acer TravelMate 4060 (dual booting with XP), and no matter what I do I cannot connect to my wireless network.

I have installed the correct driver with NdisWrapper, and it tells me the driver is installed and the hardware is working.  I installed network-manager, but it does not offer me any choices for wireless networks.

If anyone can help me or point me in the right direction I'd really appreciate it.  Thanks.

Try installing acer_acpi
[http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html](http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html)

If you are using kernel 2.6.18.x do this:
"do compile acer_acpi not only with "make" but with "make acer_acpi.ko",
as make does not recognize the kernel correctly. After this copy the *.ko
to /lib/modules/<kernelversion>/kernel/driver/char/ and make a sudo depmod -a." and then sudo modprobe acer_acpi

---

### Post by 'Orrible Cabbage on 2006-11-06
I tried both the way described on the acer_acpi site and your method listed above and both produced the same result:
```
FATAL: Error inserting acer_acpi (/lib/modules/2.6.17-10-386/extra/acer_acpi.ko): No such device
```

---

### Post by 'Orrible Cabbage on 2006-11-06
Help?  Anyone?

It keeps saying there is no such device, when I know the device is there.

---

### Post by skirkpatrick on 2006-11-06
When you have Network Manager running, you need to make some changes to another file.  Do **sudo gedit /etc/network/interfaces**.  Comment out every line by putting a **#** at the beginning of the line except for any that have **lo** in them.  For example:
> 
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp


and restart your machine.  Network Manager won't use any device that's defined in /etc/network/interfaces.

---

### Post by thegitksan on 2006-11-07
What is the wireless in your Acer? I have an Acer 3613LCi. My wireless is Broadcom 802.11g. It seems to work just fine for WinXP, and in Ubuntu 6.10 the OS sees the card also. And I have tried both Network Manager as well as /System/Adminstration/Networking menu item, and I can't get it to connect either.

I'll try a few of these suggestions listed here. If I get any results, I'll let you know.

---

