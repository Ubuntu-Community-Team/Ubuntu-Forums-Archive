---
title: "DVD burning"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by chazn85 on 2010-01-20
Evening all,

Im running Karmic 64 bit dual boot with Windows XP (never used) and having a problem with burning any sort of DVD to any sort of media with brasero.  By "any sort of media" i mean DVD +R/ -R & RW only in ubuntu.

The two main errors are as follows (highlighted in bold).

```


BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=8
	-use-the-force-luke=tracksize:1192217
	-use-the-force-luke=tty
	-Z
	/dev/sr0=/home/chaz/Videos/SawVI/SawVI.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/chaz/Videos/SawVI/SawVI.iso of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
**BraseroGrowisofs stderr: :-[ PERFORM OPC failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error**
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 133
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
**Session error : unknown (brasero_burn_record brasero-burn.c:2811)**


```

Having search the Internet and forums suggestions such as updating driver firmware have been done.  

The output of lshw is as follows

```

H/W path           Device      Class       Description
======================================================
                               system      Dell XPS420
/0                             bus         0TP406
/0/0                           memory      64KiB BIOS
/0/400                         processor   Intel(R) Core(TM)2 Quad CPU    Q6600 
/0/400/700                     memory      32KiB L1 cache
/0/400/701                     memory      8MiB L2 cache
/0/1000                        memory      4GiB System Memory
/0/1000/0                      memory      1GiB DIMM DDR2 Synchronous 800 MHz (1
/0/1000/1                      memory      1GiB DIMM DDR2 Synchronous 800 MHz (1
/0/1000/2                      memory      1GiB DIMM DDR2 Synchronous 800 MHz (1
/0/1000/3                      memory      1GiB DIMM DDR2 Synchronous 800 MHz (1
/0/100                         bridge      82X38/X48 Express DRAM Controller
/0/100/1                       bridge      82X38/X48 Express Host-Primary PCI Ex
/0/100/1/0                     display     G84 [GeForce 8600 GTS]
/0/100/6                       bridge      82X38/X48 Express Host-Secondary PCI 
/0/100/19          eth0        network     82566DC-2 Gigabit Network Connection
/0/100/1a                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.2                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1b                      multimedia  82801I (ICH9 Family) HD Audio Control
/0/100/1c                      bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1d                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.2                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1e                      bridge      82801 PCI Bridge
/0/100/1e/a                    bus         TSB43AB22/A IEEE-1394a-2000 Controlle
/0/100/1f                      bridge      82801IR (ICH9R) LPC Interface Control
/0/100/1f.2        scsi0       storage     82801 SATA RAID Controller
/0/100/1f.2/0      /dev/sda    disk        320GB WDC WD3200AAKS-7
/0/100/1f.2/0/1    /dev/sda1   volume      298GiB Windows NTFS volume
/0/100/1f.2/1      /dev/sdb    disk        320GB WDC WD3200AAKS-7
/0/100/1f.2/1/1    /dev/sdb1   volume      287GiB EXT3 volume
/0/100/1f.2/1/2    /dev/sdb2   volume      10GiB Extended partition
/0/100/1f.2/1/2/5  /dev/sdb5   volume      10GiB Linux swap / Solaris partition
/0/100/1f.2/0.0.0  /dev/cdrom  disk        DVD writer
/0/100/1f.3                    bus         82801I (ICH9 Family) SMBus Controller
/0/1               scsi6       storage     
/0/1/0.0.0         /dev/sdc    disk        USB   HS-CF Card
/0/1/0.0.0/0       /dev/sdc    disk        
/0/1/0.0.1         /dev/sdd    disk        USB   HS-xD/SM
/0/1/0.0.1/0       /dev/sdd    disk        
/0/1/0.0.2         /dev/sde    disk        USB   HS-MS Card
/0/1/0.0.2/0       /dev/sde    disk        
/0/1/0.0.3         /dev/sdf    disk        USB   HS-SD Card
/0/1/0.0.3/0       /dev/sdf    disk        
/0/2               scsi7       storage     
/0/2/0.0.0         /dev/sdg    disk        SCSI Disk
/1                 vboxnet0    network     Ethernet interface


```

and hdparm -i on the dvd writer shown above as follows

```


/dev/cdrom:
 HDIO_DRIVE_CMD(identify) failed: Bad address

 Model=PBDS, FwRev=2D15, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  *sdma0 *sdma1 *sdma2 sdma? mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


```

Can anyone shed any light on what to try next etc?  

Thanks

---

### Post by lemmy999 on 2010-01-20
I'd try k3b. Its a good burning prog and works well for most of the kit out there.

---

### Post by chazn85 on 2010-01-20
> **chazn85 said:**
> Evening all,

Im running Karmic 64 bit dual boot with Windows XP (never used) and having a problem with burning any sort of DVD to any sort of media with brasero.  By "any sort of media" i mean DVD +R/ -R & RW only in ubuntu.

The two main errors are as follows (highlighted in bold).

```


BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=8
	-use-the-force-luke=tracksize:1192217
	-use-the-force-luke=tty
	-Z
	/dev/sr0=/home/chaz/Videos/SawVI/SawVI.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/chaz/Videos/SawVI/SawVI.iso of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
**BraseroGrowisofs stderr: :-[ PERFORM OPC failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error**
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 133
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
**Session error : unknown (brasero_burn_record brasero-burn.c:2811)**


```

Having search the Internet and forums suggestions such as updating driver firmware have been done.  

The output of lshw is as follows

```

H/W path           Device      Class       Description
======================================================
                               system      Dell XPS420
/0                             bus         0TP406
/0/0                           memory      64KiB BIOS
/0/400                         processor   Intel(R) Core(TM)2 Quad CPU    Q6600 
/0/400/700                     memory      32KiB L1 cache
/0/400/701                     memory      8MiB L2 cache
/0/1000                        memory      4GiB System Memory
/0/1000/0                      memory      1GiB DIMM DDR2 Synchronous 800 MHz (1
/0/1000/1                      memory      1GiB DIMM DDR2 Synchronous 800 MHz (1
/0/1000/2                      memory      1GiB DIMM DDR2 Synchronous 800 MHz (1
/0/1000/3                      memory      1GiB DIMM DDR2 Synchronous 800 MHz (1
/0/100                         bridge      82X38/X48 Express DRAM Controller
/0/100/1                       bridge      82X38/X48 Express Host-Primary PCI Ex
/0/100/1/0                     display     G84 [GeForce 8600 GTS]
/0/100/6                       bridge      82X38/X48 Express Host-Secondary PCI 
/0/100/19          eth0        network     82566DC-2 Gigabit Network Connection
/0/100/1a                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.2                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1b                      multimedia  82801I (ICH9 Family) HD Audio Control
/0/100/1c                      bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1d                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.2                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1e                      bridge      82801 PCI Bridge
/0/100/1e/a                    bus         TSB43AB22/A IEEE-1394a-2000 Controlle
/0/100/1f                      bridge      82801IR (ICH9R) LPC Interface Control
/0/100/1f.2        scsi0       storage     82801 SATA RAID Controller
/0/100/1f.2/0      /dev/sda    disk        320GB WDC WD3200AAKS-7
/0/100/1f.2/0/1    /dev/sda1   volume      298GiB Windows NTFS volume
/0/100/1f.2/1      /dev/sdb    disk        320GB WDC WD3200AAKS-7
/0/100/1f.2/1/1    /dev/sdb1   volume      287GiB EXT3 volume
/0/100/1f.2/1/2    /dev/sdb2   volume      10GiB Extended partition
/0/100/1f.2/1/2/5  /dev/sdb5   volume      10GiB Linux swap / Solaris partition
/0/100/1f.2/0.0.0  /dev/cdrom  disk        DVD writer
/0/100/1f.3                    bus         82801I (ICH9 Family) SMBus Controller
/0/1               scsi6       storage     
/0/1/0.0.0         /dev/sdc    disk        USB   HS-CF Card
/0/1/0.0.0/0       /dev/sdc    disk        
/0/1/0.0.1         /dev/sdd    disk        USB   HS-xD/SM
/0/1/0.0.1/0       /dev/sdd    disk        
/0/1/0.0.2         /dev/sde    disk        USB   HS-MS Card
/0/1/0.0.2/0       /dev/sde    disk        
/0/1/0.0.3         /dev/sdf    disk        USB   HS-SD Card
/0/1/0.0.3/0       /dev/sdf    disk        
/0/2               scsi7       storage     
/0/2/0.0.0         /dev/sdg    disk        SCSI Disk
/1                 vboxnet0    network     Ethernet interface


```

and hdparm -i on the dvd writer shown above as follows

```


/dev/cdrom:
 HDIO_DRIVE_CMD(identify) failed: Bad address

 Model=PBDS, FwRev=2D15, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  *sdma0 *sdma1 *sdma2 sdma? mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


```

Can anyone shed any light on what to try next etc?  

Thanks

Mods, can this be moved to a more suitable forum in light of limited response.

Thanks

---

### Post by chazn85 on 2010-01-20
> **lemmy999 said:**
> I'd try k3b. Its a good burning prog and works well for most of the kit out there.

Thanks for the response, the main reason i dont want to install k3b is the space it takes up.  200meg at the last count when i tried to install it.

Thanks

---

### Post by LowSky on 2010-01-20
What kind of drive is it SATA or older IDE?

Have you tried connecting to another port on the motherboard?

Have you tried to burn to other media or another group of files?

---

### Post by chazn85 on 2010-01-20
> **LowSky said:**
> What kind of drive is it SATA or older IDE?

Have you tried connecting to another port on the motherboard?

Have you tried to burn to other media or another group of files?

Not entirely sure what sort of drive it is hence i posted some diagnostics.  I would assume SATA.  I have tried other sorts of media but not other ports on the motherboard.   Will give this a go although i think its more a 64 bit problem as ive never had any problems with 32bit on my laptop

Thanks again

---

### Post by LowSky on 2010-01-20
64bit would not cause these issues, and my last post is kinda voided since your using a laptop.

have you updated your pc since installing 64bit? have you rebooted?

The issue you are having is an odd one, and from whaI find on the web seemingly disappears after an update

---

### Post by chazn85 on 2010-01-20
> **LowSky said:**
> 64bit would not cause these issues, and my last post is kinda voided since your using a laptop.

have you updated your pc since installing 64bit? have you rebooted?

The issue you are having is an odd one, and from whaI find on the web seemingly disappears after an update

I have a laptop on 32 bit which works fine.  I have updated my workstation to 9.10  which runs 64 bit but this is the workstation in which i cant burn.  I run the latest updates all all of my PC's the 64bit machine is the only one with the issue.  Ive also tried burning in VBOX with passthrough with no luck

Thanks

---

