---
title: "Acx Firmware problem"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by Vampirlinux on 2006-09-06
Hi, 

I've a Usr2210 PCMCIA wireless card that doesn't work on Ubuntu.
Here is my  dmesg | grep acx:
[17179604.672000] acx: Loaded combined PCI/USB driver, firmware_ver=default
[17179604.672000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[17179605.288000] acx: found ACX100-based wireless network card at 0000:02:00.0, irq:169, phymem1:0x32010000, phymem2:0x32000000, mem1:0xe09d2000, mem1_size:4096, mem2:0xe0b40000, mem2_size:65536
[17179605.416000] acx: firmware image 'acx/default/tiacx100c11' was not provided. Check your hotplug scripts
[17179606.496000] acx: form factor 0x00 (unspecified), radio type 0x11 (RFMD), EEPROM version 0x04, uploaded firmware 'Rev 1.9.8.b' (0x01020505)
[17179606.496000] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 19 and Linux 2.6.15-26-386
[17179606.496000] usbcore: registered new driver acx_usb
[17180051.588000] acx: found ACX100-based wireless network card at 0000:02:00.0, irq:169, phymem1:0x32010000, phymem2:0x32000000, mem1:0xe09d2000, mem1_size:4096, mem2:0xe0b40000, mem2_size:65536
[17180051.904000] acx: firmware image 'acx/default/tiacx100c11' was not provided. Check your hotplug scripts
[17180053.000000] acx: form factor 0x00 (unspecified), radio type 0x11 (RFMD), EEPROM version 0x04, uploaded firmware 'Rev 1.9.8.b' (0x01020505)
[17180053.000000] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 19 and Linux 2.6.15-26-386

I can't Use ndiswrapper because i dont have any .inf archive.](*,) 
The card is properly configured and i have signal stregth but it doesn't connect.

Any One can Help?
Tanks in advance

---

### Post by Vampirlinux on 2006-09-06
Problem Solved........:-# [COLOR="Red"]**Forget this post **[/COLOR]

---

