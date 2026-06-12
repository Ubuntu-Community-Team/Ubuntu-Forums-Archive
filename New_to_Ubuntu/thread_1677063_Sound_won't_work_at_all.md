---
title: "Sound won't work at all"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by mattone on 2011-01-28
I'm new to all of this and i just got ubuntu 10.4 LTS and i have no sound coming out of speakers at all.
how can i fix this

---

### Post by anglican on 2011-01-28
> **mattone said:**
> I'm new to all of this and i just got ubuntu 10.4 LTS and i have no sound coming out of speakers at all.
how can i fix thisYou're going to have to give a bit more detail here to stand any chance of getting help... like which computer/sound card are you using. The output from ```
sudo lspci
``` would be a start. If there's a speaker icon on your panel, try clicking on it and seeing what the volume is set to.

H

---

### Post by Skrapp_Jaw on 2011-02-01
Actually. I installed 10.04 on that laptop. It is an HP G42-410us Laptop. 64 bit. intel chipset. He talked to me about it some. It seems when he puts the headphones in and then takes them out, his front speakers will not come back on. restart had no effect.

---

### Post by anglican on 2011-02-01
> **Skrapp_Jaw said:**
> Actually. I installed 10.04 on that laptop. It is an HP G42-410us Laptop. 64 bit. intel chipset. He talked to me about it some. It seems when he puts the headphones in and then takes them out, his front speakers will not come back on. restart had no effect.Have a look at what the ALSA mixer shows. I use gnome-alsamixer, but there are other options that may be installed (e.g. aumix), which may show headphones on and speakers muted. 

H

---

### Post by mattone on 2011-03-07
I have my pal here showing me how to help you help me. Here is the terminal output.

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by anglican on 2011-03-08
> **mattone said:**
> I have my pal here showing me how to help you help me. Here is the terminal output.

```

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)


```Try:```
sudo aptitude install linux-backports-modules-alsa-lucid-generic
```
reboot and see if that fixes the problem.

H

---

### Post by mastablasta on 2011-03-08
if not, then upgrade to version 10.10 which has newer ALSA (linux sound card drivers) installed by default.

---

### Post by khan187 on 2011-10-05
[SIZE=4]**my head phones work but my speakers dont on my hp G42 after installing ubuntu. please help!**[/SIZE]

---

### Post by computerandu on 2011-10-05
> **khan187 said:**
> [SIZE=4]**my head phones work but my speakers dont on my hp G42 after installing ubuntu. please help!**[/SIZE]

Try this:
[http://computerandu.wordpress.com/2011/06/19/how-to-solve-no-sound-through-laptop-integrated-speakers-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/06/19/how-to-solve-no-sound-through-laptop-integrated-speakers-in-ubuntu-11-04/)

---

