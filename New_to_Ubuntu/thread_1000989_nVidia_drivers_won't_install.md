---
title: "nVidia drivers won't install"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by redhotchilis64 on 2008-12-03
I can't get desktop effects enabled in 8.10. I tried to install the driver via Envy, but I got an error. When I ran the log it told me to check, I got "ENVY ERROR: Your Operative System does not seem to be supported by Envy". I have no idea what this means... any help? Thanks.

---

### Post by oldos2er on 2008-12-03
Which video card? Did you go to System, Administration, Hardware Drivers to see if you could install the drivers from there?

---

### Post by Michael.Godawski on 2008-12-03
It would be nice to know your hardware, especially your graphic card.
```
sudo lshw -short
sudo lshw -C display

```

---

### Post by adamitj on 2008-12-03
Why don't you try to install nVidia drivers from the built-in hardware assistant (System-->Administration-->Hardware Drivers)?

The driver is the same one that you can download from the nVidia Website, and the fx are enabled in the same way.

In the past I used to compile my own drivers from nVidia sources, and after too much headaches I realize that ubuntu can install proprietary drivers better than compiling by myself.

TIP: be sure to run a [FONT="Fixedsys"]sudo apt-get update[/FONT] (must be connected to an internet connection) before open the hardware drivers window.

---

### Post by redhotchilis64 on 2008-12-03
> **oldos2er said:**
> Which video card? Did you go to System, Administration, Hardware Drivers to see if you could install the drivers from there?

It's an nVidia, and yes. I had two different choices of drivers to install. nVidia accelerated graphics driver version 173 (which is recommended), and I have version 96. I've tried activating both of them, and I get the same problem with each of them. The desktop effects won't work.

---

### Post by oldos2er on 2008-12-03
Yes, I figured it was Nvidia from the thread title. Which Nvidia card is it?

---

### Post by redhotchilis64 on 2008-12-03
> **Michael.Godawski said:**
> It would be nice to know your hardware, especially your graphic card.
```
sudo lshw -short
sudo lshw -C display

```

here's what I have:
H/W path             Device      Class          Description
===========================================================
                                 system         D300A
/0                               bus            D845GVSR
/0/0                             memory         64KiB BIOS
/0/4                             processor      Intel(R) Pentium(R) 4 CPU 2.80GH
/0/4/5                           memory         8KiB L1 cache
/0/4/6                           memory         512KiB L2 cache
/0/2f                            memory         1GiB System Memory
/0/2f/0                          memory         512MiB DIMM DDR Synchronous 266 
/0/2f/1                          memory         512MiB DIMM DDR Synchronous 266 
/0/100                           bridge         82845G/GL[Brookdale-G]/GE/PE DRA
/0/100/2                         display        82845G/GL[Brookdale-G]/GE Chipse
/0/100/1d                        bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH
/0/100/1d.1                      bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH
/0/100/1d.2                      bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH
/0/100/1d.7                      bus            82801DB/DBM (ICH4/ICH4-M) USB2 E
/0/100/1e                        bridge         82801 PCI Bridge
/0/100/1e/1                      display        NV34 [GeForce FX 5200]
/0/100/1e/2                      communication  HSF 56k HSFi Modem
/0/100/1e/8          eth0        network        82801DB PRO/100 VE (LOM) Etherne
/0/100/1f                        bridge         82801DB/DBL (ICH4/ICH4-L) LPC In
/0/100/1f.1          scsi0       storage        82801DB (ICH4) IDE Controller
/0/100/1f.1/0        /dev/sda    disk           60GB WDC WD600BB-00JH
/0/100/1f.1/0/1      /dev/sda1   volume         55GiB Windows NTFS volume
/0/100/1f.1/1        /dev/cdrom  disk           CD-RW  CRX320E
/0/100/1f.1/1/0      /dev/cdrom  disk           
/0/100/1f.1/0.1.0    /dev/sdb    disk           80GB WDC WD800JB-00JJ
/0/100/1f.1/0.1.0/1  /dev/sdb1   volume         74GiB Windows NTFS volume
/0/100/1f.3                      bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH
/0/100/1f.5                      multimedia     82801DB/DBL/DBM (ICH4/ICH4-L/ICH
/0/1                 scsi2       storage        
/0/1/0.0.0           /dev/sdc    disk           SCSI Disk
/0/1/0.0.1           /dev/sdd    disk           SCSI Disk
/0/1/0.0.2           /dev/sde    disk           SCSI Disk
/0/1/0.0.3           /dev/sdf    disk           SCSI Disk
/1                   wlan0       network        Wireless interface
/2                   pan0        network        Ethernet interface
jloganw@ubuntu:~$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
  *-display UNCLAIMED
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: nVidia Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=248 maxlatency=1 mingnt=5

---

### Post by redhotchilis64 on 2008-12-03
My problem is the desktop effects won't enable. I think the driver may be installed and working properly, but for some reason anything that has to do with Compiz Fusion won't work.

---

### Post by oldos2er on 2008-12-03
> **redhotchilis64 said:**
> It's an nVidia, and yes. I had two different choices of drivers to install. nVidia accelerated graphics driver version 173 (which is recommended), and I have version 96. I've tried activating both of them, and I get the same problem with each of them. The desktop effects won't work.

 The video driver version 173 is the right one for your card. Can you give a little more detail about your desktop effects? How exactly are you trying to enable them?

---

### Post by ajgreeny on 2008-12-03
It looks as if you have an onboard video card as well as the nvidia one.  You may need to ensure that the onboard card is disabled in bios first, I think.

*-display UNCLAIMED     
       description: VGA compatible controller
       **product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device**
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
  *-display UNCLAIMED
       description: VGA compatible controller
       **product: NV34 [GeForce FX 5200]**
       vendor: nVidia Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=248 maxlatency=1 mingnt=5

---

### Post by redhotchilis64 on 2008-12-03
> **oldos2er said:**
> The video driver version 173 is the right one for your card. Can you give a little more detail about your desktop effects? How exactly are you trying to enable them?

I'm right clicking on the desktop, going down to "change desktop background", clicking on the "visual effects" tab, and trying anything but "none". No effects is automatically selected, and it won't let me select anything else. It says it cannot be enabled.

---

