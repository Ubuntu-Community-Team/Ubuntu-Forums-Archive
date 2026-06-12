---
title: "[SOLVED] Dell Inspiron 1720"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by tompickles on 2008-09-11
I have a Dell Inspiron 1720, loaded up with windows vista. installed ubuntu 8.04 with WUBI so i dont trash the partition by accident.
when i loaded it up, it didnt detect my wireless card at all.... VERY annoying.... please help me

thanks in advance

---

### Post by Crymsin_Veggie_Eater on 2008-09-11
What are the specs on your wireless card?

---

### Post by tompickles on 2008-09-12
according to Live Chat on Dell website, my sales advisor said:

Dell wireless 1395 802 b/g card

---

### Post by ozanamn on 2008-09-12
Goto a Terminal and type lspci and post the result here,

Regards,
Oz

---

### Post by tompickles on 2008-09-12
will do - after i reinstall :)

---

### Post by tompickles on 2008-09-13
lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

---

### Post by PinkFloyd102489 on 2008-09-13
Try the Restricted Drivers Manager. The "wl" driver should work for your chipset. Otherwise, you'll have to use ndiswrapper.

---

### Post by tompickles on 2008-09-14
went into Restricted Drivers manager. It said wl was enabled, but not in use.... but my wireless switch is on, though whenever i turn it off, the little light to say its status stays on.......

HELP!!!!

---

### Post by tompickles on 2008-09-14
Bump

---

### Post by tompickles on 2008-09-15
Bump! Would really like to fix this please!

---

### Post by panhandle on 2008-09-15
Sorry, just reread your post and noticed that your adapter wasn't detected at all.

please post results of: 

```
lshw -C network
```

______Disregard above question________

On second thought...you might want to perform a quick search for your wireless card on these boards. 

There are, sorry to say, many posts about the 1395. The above poster was correct and it looks like you have some work to do.

---

### Post by ozanamn on 2008-09-15
Have you tried to install the card with ndiswrapper?

---

### Post by tompickles on 2008-09-15
ndiswrapper - i can do that, as long as you point me to an easy to follow tutorial please.

thank you for all the advice

---

### Post by panhandle on 2008-09-15
This should get you started:

[http://ubuntuforums.org/showthread.php?t=859580&highlight=ndiswrapper+1395](http://ubuntuforums.org/showthread.php?t=859580&highlight=ndiswrapper+1395)

and a troubleshooting guide in case something doesn't work:

[http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper+1395](http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper+1395)

---

### Post by tompickles on 2008-10-25
UPDATE: Wireless now works...... just randomly! Installed natively, perhaps that is why.

---

