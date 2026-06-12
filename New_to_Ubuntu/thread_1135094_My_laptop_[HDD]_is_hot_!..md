---
title: "My laptop [HDD] is hot !."
date: 2009-04-24
forum: New to Ubuntu
---

### Post by lipin on 2009-04-24
Hello,

I've just installed new netbook ubuntu 9.04 nice idea! but nah i switched to normal mode its too buggy.

My problem is ubuntu makes my laptop Acer 5920G hot under left palm. CPU temperature is 46C (acpi -V) GPU about 60 (nvidia-settings) HDD 46 (sudo hddtemp /dev/sda). All numbers seems ok and windows alike so why o why it is so hot compared to vista! I want to run MATLAB under linux due to lower memory usage but now I cant work comfortable.

I suspect that under my left palm is HDD how to fix it?

Greetings
Lipin

---

### Post by Alterax on 2009-04-24
Could be a number of things.  Applying a couple of laws of physics can give us some answers:  It's hot because it's consuming a lot of power.  The logical thing to do is to reduce the power consumption (which is nice on the batteries).

First off, I usually add the option noatime to my main partition's entry in /etc/fstab.  I really could care less on my laptop when I last accessed a file (as opposed to modifying it), so there's really no need to write to the drive every single time. The noatime flag handles that.

Next, download and install the utility powertop.  It's in the standard repo; invoke it from the terminal through sudo powertop.  Let it run, and follow its instructions; usually it can make alterations to your power consumption for you.  Note it gives a suggestion about every 10-20 seconds, so the first go may take a bit, but the changes are cumulative and they tend to stick.

After that, it should purr like a kitten.

---

### Post by lipin on 2009-04-27
I run couple of test with hdparm -B 1,127,254 -M 128 non of this settings seems to work -B 1 is spinning down my hdd very often but temperature stays almost same like in -B 255 (no management). Temperatures are about 5-9C higher then in Windows Vista.

Greetings

EDIT: I did try powertop too

Here is my HDD info:
hdparm -iI /dev/sda
```

 Model=WDC WD2500BEVS-22UST0                   , FwRev=01.01A01, SerialNo=     WD-WXCY07064172
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=488397168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode


ATA device, with non-removable media
	Model Number:       WDC WD2500BEVS-22UST0                   
	Serial Number:      WD-WXCY07064172
	Firmware Revision:  01.01A01
Standards:
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  488397168
	device size with M = 1024*1024:      238475 MBytes
	device size with M = 1000*1000:      250059 MBytes (250 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: 127
	Recommended acoustic management value: 128, current value: 128
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	   *	Advanced Power Management feature set
	    	SET_MAX security extension
	   *	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	   *	64-bit World wide name
	   *	IDLE_IMMEDIATE with UNLOAD
	   *	Segmented DOWNLOAD_MICROCODE
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	    	DMA Setup Auto-Activate optimization
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
	    	unknown 206[13] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
	not	supported: enhanced erase
	92min for SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 50014ee2ab687c9b
	NAA		: 5
	IEEE OUI	: 14ee
	Unique ID	: 2ab687c9b
Checksum: correct
```

---

