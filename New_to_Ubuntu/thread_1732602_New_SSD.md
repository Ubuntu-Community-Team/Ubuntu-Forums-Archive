---
title: "New SSD"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by theller on 2011-04-18
I got a new SSD 30g that I want to use for OS (Ubuntu 10.04). I also have a 500g external drive for my music, videos, documents and pictures. In the two user accounts I linked to those folders on the external so we share the same folders on the external. Should I have moved the whole home folder to the external? Should I move /tmp or any other folders to save from writing to the SSD?

I followed the advice in this thread but I don't know if it is making a difference: [http://ubuntuforums.org/showthread.php?t=1709189](http://ubuntuforums.org/showthread.php?t=1709189)

I am not sure if I want to follow the advise on this link:
[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

Is there anything else I could do to speed up and slim down the SSD.

Kinston SSDnowV series 30g
WD Scorpio Black 500g
GSkill 2x2g 
Jetway Minitop HTPC

---

### Post by Paqman on 2011-04-18
> **theller said:**
> In the two user accounts I linked to those folders on the external so we share the same folders on the external. Should I have moved the whole home folder to the external?

Nope, you can just link the folders, it does the same thing. Doing it the way you have gives you the advantage that all your settings are still on the SSD, which makes the system faster.


> Should I move /tmp or any other folders to save from writing to the SSD?

Yep, can't hurt. You've got plenty of RAM, you might as well put it to use.


> 
I am not sure if I want to follow the advise on this link:
[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)


Nope, not a good idea IMO. What you do want to do however is enable TRIM for your drive. Open up the filesystem table:
```
gksudo gedit /etc/fstab
```

and on the lines that mount your root and home partitions add the option "discard" (without the quotes).

---

### Post by theller on 2011-04-19
Thanks for the input.

I tried using sudo nautilus to move /tmp to the HD and the system crashed.

---

### Post by Paqman on 2011-04-19
> **theller said:**
> Thanks for the input.

I tried using sudo nautilus to move /tmp to the HD and the system crashed.

Yeah, it doesn't really work like that. The file /etc/fstab is what tells the system where to mount storage devices in the filesystem. If you want to shift a folder like /tmp to RAM, then you need to add an entry to /etc/fstab and reboot.

---

### Post by Locke_99GS on 2011-04-19
/tmp is mounted and being used by the system. If you just up and move it, it won't exist at it's previous mountpoint, and the system doesn't know where you moved it to. You must do that in fstab.

---

### Post by wolfen69 on 2011-04-19
> **Paqman said:**
> What you do want to do however is enable TRIM for your drive.

In recent kernels, TRIM is automatically enabled.

---

### Post by ikt on 2011-04-19
Make a separate home partition, everything else doesn't really matter.


```
sudo hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
	Model Number:       OCZ-VERTEX2                             
	Serial Number:      OCZ-LLP01UOJBSC6E8TO
	Firmware Revision:  1.10    
	Transport:          Serial
Standards:
	Used: unknown (minor revision code 0x0028) 
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  234441648
	LBA48  user addressable sectors:  234441648
	Logical  Sector size:                   512 bytes
	Physical Sector size:                   512 bytes
	Logical Sector-0 offset:                  0 bytes
	device size with M = 1024*1024:      114473 MBytes
	device size with M = 1000*1000:      120034 MBytes (120 GB)
	cache/buffer size  = unknown
	Nominal Media Rotation Rate: Solid State Device
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 1
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
	    	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	   *	64-bit World wide name
	   *	IDLE_IMMEDIATE with UNLOAD
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	DMA Setup Auto-Activate optimization
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	   *	Data Set Management TRIM supported
	   *	Deterministic read data after TRIM
Security: 
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
	not	supported: enhanced erase
Logical Unit WWN Device Identifier: 5e83a97f2a7ffd37
	NAA		: 5
	IEEE OUI	: e83a97
	Unique ID	: f2a7ffd37
```

I manually entered "discard" in my fstab though, might try without it later.

---

### Post by Paqman on 2011-04-19
> **wolfen69 said:**
> In recent kernels, TRIM is automatically enabled.

Are you sure? Newer kernels have TRIM support, but you still have to add the option in fstab. Or is this not necessary on really recent kernels?

---

### Post by theller on 2011-04-21
Here is my fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f5b72000-d97e-4cbc-beb8-133f9bbf517a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4fe46757-4572-4577-8668-b0a0414f35b0 none            swap    sw              0       0
tmpfs /tmp tmpfs nodev,nosuid,noexec,mode=1777 0 0

The last line is what I added in. What do I need to change to make /temp go to ram?

---

### Post by Locke_99GS on 2011-04-21
That last line will do it. Did you reboot since you changed fstab? Once you do, it'll create a ramdisk and mount it at /tmp.

Run the *df* command to see if its working.
```
df
```

---

### Post by theller on 2011-04-21
Thanks!

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             27616124   3996836  22216460  16% /
none                   2054820       392   2054428   1% /dev
none                   2059032       196   2058836   1% /dev/shm
tmpfs                  2059032        12   2059020   1% /tmp
none                   2059032        84   2058948   1% /var/run
none                   2059032         0   2059032   0% /var/lock
none                   2059032         0   2059032   0% /lib/init/rw
/dev/sdc1              3864064   1457408   2406656  38% /media/6338-3261
/dev/sdb1            471793992  37802124 410026124   9% /media/3ae8526e-34ef-4015-ab78-a59a9a32aa27

What else can I move?

---

### Post by Locke_99GS on 2011-04-21
Anything you want to be really fast and temporary.

For example, here's mine:
```

locke@cerberus:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             734G   99G  598G  15% /
none                  3.9G  308K  3.9G   1% /dev
none                  4.0G  216K  4.0G   1% /dev/shm
tmpfs                 4.0G   36K  4.0G   1% /tmp
none                  4.0G  412K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
tmpfs                 4.0G     0  4.0G   0% /var/tmp
tmpfs                 4.0G  652K  4.0G   1% /var/log
tmpfs                 4.0G     0  4.0G   0% /var/log/apt

```

---

### Post by theller on 2011-04-21
If I were to move /var/tmp would I add this to fstab?

tmpfs /var/tmp tmpfs nodev,nosuid,noexec,mode=1777 0 0

---

### Post by Locke_99GS on 2011-04-21
That ought to work fine.

---

### Post by theller on 2011-04-21
It worked! Thanks again.

---

### Post by theteju on 2011-04-22
> **theller said:**
> It worked! Thanks again.

I am looking to buy a small SSD and just want it for stable performance. I am kind of lost reading this thread although it says solved. 

Please be kind to write step by step tutorial for such a set up.

Thanks in advance.

---

### Post by theller on 2011-04-22
I bought a small SSD drive, Kingston ssdnow Vseries 30gb, and I have  only ubuntu 10.04 on it. I have another drive that I moved all my music  and videos to. I did this because I read that constantly writing to an  SSD will shorten its life. Besides they don't write very fast, they only  read very fast. They read really fast. Another bonus is since there is  no moving parts, there is no heat. That was my main objective when I  bought the SSD because I have a [mini computer]("http://www.jetway.com.tw/jw/Barebone_view.asp?productid=760&proname=JBC600C99352W-BW%20%28Mini-top%29") and heat was an issue. It's been over a month and I have had no problems with it - stable, fast and cool.

I marked the thread solved because Locke_99GS helped me to see that I  had a set up a folder with temporary files to write to the RAM instead  of the SSD. This will lengthen the life of the SSD and speed up the  computer. I also got help changing other files to write to the RAM.

Did you want a step by step for linking to folders on another drive or how to have temporary folders write to RAM?

---

### Post by theteju on 2011-04-23
> **theller said:**
> I bought a small SSD drive, Kingston ssdnow Vseries 30gb, and I have  only ubuntu 10.04 on it. I have another drive that I moved all my music  and videos to. I did this because I read that constantly writing to an  SSD will shorten its life. Besides they don't write very fast, they only  read very fast. They read really fast. Another bonus is since there is  no moving parts, there is no heat. That was my main objective when I  bought the SSD because I have a [mini computer]("http://www.jetway.com.tw/jw/Barebone_view.asp?productid=760&proname=JBC600C99352W-BW%20%28Mini-top%29") and heat was an issue. It's been over a month and I have had no problems with it - stable, fast and cool.

I marked the thread solved because Locke_99GS helped me to see that I  had a set up a folder with temporary files to write to the RAM instead  of the SSD. This will lengthen the life of the SSD and speed up the  computer. I also got help changing other files to write to the RAM.

Did you want a step by step for linking to folders on another drive or how to have temporary folders write to RAM?

yes and yes, I would like to have steps to come up with stable set up with SSD. Please write down if you dont mind the steps you followed in order. I have seen some posts online to set up ubuntu on SSD but they were written on 2009. must be outdated.

---

