---
title: "Audio drivers?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Crasken on 2009-02-09
Will the audio drivers from my Windows XP restore disk work with Ubuntu 8.10 (I have a feeling they won't)? If not, where would I download the proper audio drivers for the speakers in my tablet PC?

Edit: I already have Ubuntu downloaded, the speakers don't play anything, so I'm assuming it's an audio driver problem.

---

### Post by beno1990 on 2009-02-09
No, drivers are operating system specific.

Chances are the drivers for your device will be included in the Linux kernel package, or at least the restricted modules package.

---

### Post by Crasken on 2009-02-09
Thanks for trying to help, but the restricted packages don't help :(. Is there any other place where I can download the correct audio drivers for my computer on ubuntu?

---

### Post by Favux on 2009-02-09
Hi Crasken,

You have to tell us the make and model of your Tablet PC before anyone can help you.

---

### Post by davidsrsb on 2009-02-09
What does lspci show?

---

### Post by beno1990 on 2009-02-09
Can you show any lines from the results of the command lspci which include the word "audio"? So we have a better idea of what audio device your tablet PC actually has.

---

### Post by Crasken on 2009-02-09
My computer is a Toshiba Portege M700 Tablet PC.

When I ran the lspci command in the terminal, this is what came up.

```
cgladish@Crasken:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation Mobile PM965/GM965 MEI Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
03:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

---

### Post by davidsrsb on 2009-02-09
The Intel 82801 is normally only part of the audio chain. At first glance this lspci output is showing that an audio device is not being detected by the kernel at all
This PC appears to use a Realtek ALC883 chip

---

### Post by Crasken on 2009-02-09
So what should I do :confused:?

---

### Post by davidsrsb on 2009-02-09
The 883 seems to cause lots of problems
[https://wiki.ubuntu.com/SndHdaIntelSoundProblems](https://wiki.ubuntu.com/SndHdaIntelSoundProblems) gives a suggested solution
with model=laptop-eapd

---

### Post by Crasken on 2009-02-09
Rar, that article doesn't help, apparently my soundcard is a Realtek ALC268, and the "table of problems" says that the problem should be that output doesn't work and input works. However, neither the output nor input works, and I tried using the workarounds on the page and they didn't help :cry:

---

### Post by davidsrsb on 2009-02-10
Then this thread is relevant
[http://ubuntuforums.org/showthread.php?t=551615&page=4](http://ubuntuforums.org/showthread.php?t=551615&page=4)

---

