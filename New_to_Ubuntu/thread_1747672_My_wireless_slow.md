---
title: "My wireless slow"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by jiggajoe506 on 2011-05-02
Hey guys, I have a bit of an issue and I am too much of a rookie to figure it out. I am running ubuntu 11.04 and windows 7 as a dual boot. The problem is when running windows my internet runs very fast but when running ubuntu it is running at an almost stand still. So just to give you give you guys some specs on my  hardware:
Acer Aspire 5551
Amd Athlon II X2 processor p320 (2.1 GHz)
Acer nplify 802.11 b/g/n
Router:
Linksys WRTN160n V3

Also attached is the two speed test I ran and they are so different you would think its a joke. I wanna thank you guys in advance for all advice tips and lessons I learn from you guys.

---

### Post by kiwiluver75 on 2011-05-02
Hmm. In my computer the dual boot doesn't affect the speed of either systems.

Although, when I was using wubi, my ubuntu system was lagging like crazy. Are you sure you are not using wubi?

---

### Post by jiggajoe506 on 2011-05-02
> **kiwiluver75 said:**
> Hmm. In my computer the dual boot doesn't affect the speed of either systems.

Although, when I was using wubi, my ubuntu system was lagging like crazy. Are you sure you are not using wubi?

positive I installed it through via USB and Ubuntu has its own partrition

---

### Post by josephmills on 2011-05-02
is it when you are downloading something or does it take a long time to go site to site?

---

### Post by 5149.5 on 2011-05-03
For me, the time of day makes more difference than the OS by a long ways. Right now it is really slow and in a little while after everyone goes to bed, it will come back up to normal speed.

---

### Post by jiggajoe506 on 2011-05-03
> **josephmills said:**
> is it when you are downloading something or does it take a long time to go site to site?

It goes slow for both. Like facebook will take forever for everything to load and downloading word files can sometimes be slow. Gmail takes so long sometimes that it asks me if i wanna switch to the slower version of gmail. I no it is not the time of the day b/c i tested both one after the other on the same laptop in the same spot with the same router. Any ideas guys?

---

### Post by Karmic Kiwi on 2011-05-03
Try using traceroute to see where the delays are. It may be your router isn't wanting to play nice with Ubuntu.

---

### Post by jiggajoe506 on 2011-05-03
> **Karmic Kiwi said:**
> Try using traceroute to see where the delays are. It may be your router isn't wanting to play nice with Ubuntu.
I am not exactly sure how to use traceroute but while i start googling around on how to use it, is there any other suggestions that may help.

---

### Post by el_koraco on 2011-05-03
type 

```
lspci -k
``` in the terminal, look for the Network section, and paste that here.

---

### Post by jiggajoe506 on 2011-05-03
Ok this is what i got.

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
    Subsystem: Acer Incorporated [ALI] Device 036e
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
    Kernel modules: shpchp
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
    Subsystem: Acer Incorporated [ALI] Device 036e
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Subsystem: Acer Incorporated [ALI] Device 036e
    Kernel driver in use: ohci_hcd
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Subsystem: Acer Incorporated [ALI] Device 036e
    Kernel driver in use: ehci_hcd
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Subsystem: Acer Incorporated [ALI] Device 036e
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Subsystem: Acer Incorporated [ALI] Device 036e
    Kernel driver in use: ehci_hcd
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
    Subsystem: Acer Incorporated [ALI] Device 036e
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
    Subsystem: Acer Incorporated [ALI] Device 036e
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Acer Incorporated [ALI] Device 036e
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Acer Incorporated [ALI] Device 036e
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
    Subsystem: Acer Incorporated [ALI] Device 036e
    Kernel driver in use: ohci_hcd
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
    Subsystem: Acer Incorporated [ALI] Device 036e
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
    Subsystem: Acer Incorporated [ALI] Device 036e
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 036e
    Kernel driver in use: tg3
    Kernel modules: tg3
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Foxconn International, Inc. Device e01f
    Kernel driver in use: ath9k
    Kernel modules: ath9k

---

### Post by el_koraco on 2011-05-03
It is a known and often repeated bug with the kernel. I haven't tried this myself, but some people have, and it's worked for them. 

```
Create a file called
    /etc/modprobe.d/ath9.conf

in this file enter this
    options ath9k nohwcrypt=1

 

``` 

Save the file, of course.

After which you should reboot and hopefully your wireless speed will return. 

[Source]("http://ubuntuforums.org/showthread.php?t=1688173").

---

### Post by jiggajoe506 on 2011-05-03
> **el_koraco said:**
> It is a known and often repeated bug with the kernel. I haven't tried this myself, but some people have, and it's worked for them. 

```
Create a file called
    /etc/modprobe.d/ath9.conf

in this file enter this
    options ath9k nohwcrypt=1

 

```Save the file, of course.

After which you should reboot and hopefully your wireless speed will return. 

[Source]("http://ubuntuforums.org/showthread.php?t=1688173").
create this file in a note pad like application and create the file name and put that it in the file and after rebooting the computer will know what to do?

---

### Post by jiggajoe506 on 2011-05-03
Thats the result I get when trying to create the file

---

### Post by 5149.5 on 2011-05-03
> **jiggajoe506 said:**
> Thats the result I get when trying to create the file

Use gksudo to open the editor.

```
gksudo gedit
```

---

### Post by jiggajoe506 on 2011-05-04
alright guys I tried making the file through terminal and rebooted and i am still getting the same results. Is there a way to get another kernel? Sorry if I sound dumb but I am use to working with android phones and so i tend to treat this as if it were a phone (when it comes to terms and processes). Anyways I appreciate all the effort and help you guys have offered me.

---

### Post by seyavash on 2012-06-08
any final solution please?

---

