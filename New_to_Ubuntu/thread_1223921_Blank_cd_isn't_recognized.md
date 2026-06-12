---
title: "Blank cd isn't recognized"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2009-07-26
This is a strange one.

I have Ubuntu 9.04.

I put a blank cd in and it doesn't show up on the desk top. If I try to burn with Brasero it says there is no cd.

---

### Post by wojox on 2009-07-26
Does it recognize your cd player?

```
sudo lshw -short
```

---

### Post by desperado665 on 2009-07-26
Have you tried more than 1 disc?

---

### Post by Bigtime_Scrub on 2009-07-26
Okay....Another disk did work. That's strange...

Output of lshw -short I assume recognizes my drive as 
/dev/cdrom  disk        DVD+-RW TS-L632H

I guess the other disk was just bad and I freaked out. I dunno.

```
gary@gary-laptop:~$ sudo lshw -short
[sudo] password for gary: 
H/W path               Device      Class       Description
==========================================================
                                   system      Latitude D630
/0                                 bus         0WM416
/0/0                               memory      64KiB BIOS
/0/400                             processor   Intel(R) Core(TM)2 Duo CPU     T7
/0/400/700                         memory      32KiB L1 cache
/0/400/701                         memory      2MiB L2 cache
/0/1000                            memory      2GiB System Memory
/0/1000/0                          memory      1GiB DIMM DDR Synchronous 667 MHz
/0/1000/1                          memory      1GiB DIMM DDR Synchronous 667 MHz
/0/100                             bridge      Mobile PM965/GM965/GL960 Memory C
/0/100/1                           bridge      Mobile PM965/GM965/GL960 PCI Expr
/0/100/1/0                         display     Quadro NVS 135M
/0/100/1a                          bus         82801H (ICH8 Family) USB UHCI Con
/0/100/1a.1                        bus         82801H (ICH8 Family) USB UHCI Con
/0/100/1a.7                        bus         82801H (ICH8 Family) USB2 EHCI Co
/0/100/1b                          multimedia  82801H (ICH8 Family) HD Audio Con
/0/100/1c                          bridge      82801H (ICH8 Family) PCI Express 
/0/100/1c.1                        bridge      82801H (ICH8 Family) PCI Express 
/0/100/1c.1/0          eth1        network     BCM4312 802.11b/g
/0/100/1c.5                        bridge      82801H (ICH8 Family) PCI Express 
/0/100/1c.5/0          eth0        network     NetXtreme BCM5755M Gigabit Ethern
/0/100/1d                          bus         82801H (ICH8 Family) USB UHCI Con
/0/100/1d.1                        bus         82801H (ICH8 Family) USB UHCI Con
/0/100/1d.2                        bus         82801H (ICH8 Family) USB UHCI Con
/0/100/1d.7                        bus         82801H (ICH8 Family) USB2 EHCI Co
/0/100/1e                          bridge      82801 Mobile PCI Bridge
/0/100/1e/1                        bridge      Cardbus bridge
/0/100/1e/1.4                      bus         Firewire (IEEE 1394)
/0/100/1f                          bridge      82801HEM (ICH8M) LPC Interface Co
/0/100/1f.1            scsi3       storage     82801HBM/HEM (ICH8M/ICH8M-E) IDE 
/0/100/1f.1/0.0.0      /dev/cdrom  disk        DVD+-RW TS-L632H
/0/100/1f.2            scsi0       storage     82801HBM/HEM (ICH8M/ICH8M-E) SATA
/0/100/1f.2/0.0.0      /dev/sda    disk        120GB SAMSUNG HM121HI
/0/100/1f.2/0.0.0/1    /dev/sda1   volume      107GiB EXT3 volume
/0/100/1f.2/0.0.0/2    /dev/sda2   volume      4690MiB Extended partition
/0/100/1f.2/0.0.0/2/5  /dev/sda5   volume      4690MiB Linux swap / Solaris part
/0/100/1f.3                        bus         82801H (ICH8 Family) SMBus Contro
/1                                 power       DELL KP42289
/2                     pan0        network     Ethernet interface

```

---

