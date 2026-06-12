---
title: "Slow Boot, real slow"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Loki*PI on 2008-12-05
Recently Ubuntu 8.04 has starting taking about 8 minutes to load.  When I originally installed 8.04 the system would boot in about a minute.  I've installed all the recommended updates.  Duel core processor, 1 Gig mem.  

There seems to be a lot of time spent identifying the hard drives, but even after that the Ubuntu splash screen comes up and it just goes back and forth for 4 or 5 minutes.  

Every now and then the system boots normal, in a minute or so.

Once the system is load it seems to run normally.

Below is lshw -short

                                system      System Product Name
/0                              bus         P5GC-MX/1333
/0/0                            memory      64KiB BIOS
/0/4                            processor   Intel(R) Pentium(R) Dual  CPU  E2180  @ 
/0/4/5                          memory      64KiB L1 cache
/0/4/6                          memory      1MiB L2 cache
/0/4/7                          memory      L3 cache
/0/4/1.1                        processor   Logical CPU
/0/4/1.2                        processor   Logical CPU
/0/2e                           memory      1GiB System Memory
/0/2e/0                         memory      1GiB DIMM Synchronous 266 MHz (3.8 ns)
/0/2e/1                         memory      DIMM [empty]
/0/1                            processor   
/0/1/1.1                        processor   Logical CPU
/0/1/1.2                        processor   Logical CPU
/0/100                          bridge      82945G/GZ/P/PL Memory Controller Hub
/0/100/1                        bridge      82945G/GZ/P/PL PCI Express Root Port
/0/100/1/0                      display     RV370 [Sapphire X550 Silent]
/0/100/1/0.1                    display     RV370 secondary [Sapphire X550 Silent]
/0/100/1b                       multimedia  82801G (ICH7 Family) High Definition Aud
/0/100/1c                       bridge      82801G (ICH7 Family) PCI Express Port 1
/0/100/1c.1                     bridge      82801G (ICH7 Family) PCI Express Port 2
/0/100/1c.1/0        eth1       network     L2 100 Mbit Ethernet Adapter
/0/100/1d                       bus         82801G (ICH7 Family) USB UHCI Controller
/0/100/1d.1                     bus         82801G (ICH7 Family) USB UHCI Controller
/0/100/1d.2                     bus         82801G (ICH7 Family) USB UHCI Controller
/0/100/1d.3                     bus         82801G (ICH7 Family) USB UHCI Controller
/0/100/1d.7                     bus         82801G (ICH7 Family) USB2 EHCI Controlle
/0/100/1e                       bridge      82801 PCI Bridge
/0/100/1f                       bridge      82801GB/GR (ICH7 Family) LPC Interface B
/0/100/1f.1                     storage     82801G (ICH7 Family) IDE Controller
/0/100/1f.2          scsi2      storage     82801GB/GR/GH (ICH7 Family) SATA IDE Con
/0/100/1f.2/0.0.0    /dev/sda   disk        250GB WDC WD2500AAJS-2
/0/100/1f.2/0.0.0/1  /dev/sda1  volume      93GiB EXT3 volume
/0/100/1f.2/0.0.0/2  /dev/sda2  volume      956MiB Linux swap volume
/0/100/1f.2/0.0.0/3  /dev/sda3  volume      138GiB EXT3 volume
/0/100/1f.3                     bus         82801G (ICH7 Family) SMBus Controller

Any suggestions would be appreciated.  

Thanks

---

### Post by utnubuuser on 2008-12-05
Is this a new Hard drive, or might the hard drive be having problems?
> [http://ubuntuforums.org/showthread.php?t=160158](http://ubuntuforums.org/showthread.php?t=160158)

---

### Post by Loki*PI on 2008-12-05
It is a new HD, less than a year. There are two hard drives and a DVD, all SATA.  Also the problem is inconsistent, sometimes the system will boot in a few seconds.  Once loaded operation of the system seems normal.

---

### Post by utnubuuser on 2008-12-05
Sounds quite unusual.

Check this thread > [http://ubuntuforums.org/archive/index.php/t-448331.html](http://ubuntuforums.org/archive/index.php/t-448331.html)
sounds like a similar problem/situation/solution?

---

### Post by Loki*PI on 2008-12-05
I read the thread thanks.  Yes similar.  Haven't tried the blank DVD, that seems rather strange.  

One point in the other thread recommended a larger swap file.  I have 1Gb for swap.  Is that too small?  If so how can I enlarge it? / has 90 Gb and sets on the same physical HD.  Is there some way to expand swap?

---

### Post by philinux on 2008-12-05
Install bootchart and post an image. You'll be able to see exactly whats going on.

---

### Post by Loki*PI on 2008-12-05
Thanks I'll try that.

---

### Post by Loki*PI on 2008-12-05
I have installed bootchart.  I'm not sure what normal is but it looks like modprobe and scsi_eh_3 are both taking a long time - 150 sec. This was a fast boot for me, about 4 minutes, often it is 8 min.

As I watch the boot the system appears to hang at 
Autodetect 3rd Master - IDE HD and then again at 
Autodecect 4th Slave - IDE HD  and then again at the
Ubuntu splash screen.

I am also starting to have problems with shutdown, it freezes.

Anyone got any idea what's going on?

Thanks

---

### Post by utnubuuser on 2008-12-05
Are your hard disks set up as a Raid array?

---

### Post by Loki*PI on 2008-12-05
No nothing fancy.  Just SATA IDE.  You know what modprobe and scsi_eh_3 are?  scsi looks like its looking for scsi drives, there are no scsi drives installed, but it is spending a lot of time looking for them.  Does Ubuntu know what SATA is, it must?

---

