---
title: "New 8.10 install locks at login"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by OlPeculiar on 2009-03-28
I installed and ran Gutsy without issue for quite a while now, so I wasn't expecting trouble with this install, but...

After three failed installs (got the 94% failure of "Unable to install GRUB in HD0"), I finally tried a fourth install, where I manually partitioned the drive.  This time the install went through without incident, but now it locks at the login screen.

I've read through other threads with this type of problem, but I can't find any solutions that I can figure out.  So I'm hoping that someone might have some more "personalized" advice for me.  Here at some of my system details:

This is the exact same system that ran Gutsy, except I changed the hard drives from a single 80-Gig IDE drive to Adaptec 2610SA running (3) 1TB Caviar Blacks in RAID 5.  There's a good chance that I didn't partition the array properly, so here's the "fdisk -l" for the system:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1999.3 GB, 1999307276288 bytes
255 heads, 63 sectors/track, 243068 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b4d95

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97659103+  83  Linux
/dev/sda2           12159      243068  1854784575    5  Extended
/dev/sda5          241853      243068     9767520   82  Linux swap / Solaris
/dev/sda6           12159      241851  1845008959+  83  Linux

Partition table entries are not in disk order

```

So there you have it.  Please let me know what I might try first, and if you could be as explicit as possible, I'd appreciate it.  I'll apologize in advance for being - how shall I say? - a little light on the lingo.

Thanks very much in advance...

 - OlPeculiar

---

### Post by yeats on 2009-03-28
What are the other specs for your system (memory & processor)?  When you get to the login screen, you can actually do Ctrl-Alt-F1 to get to a text-only terminal.  How are your command-line skills?  Are you able to move around directories & open files comfortably?  grep?  less? etc.

---

### Post by OlPeculiar on 2009-03-28
You know, I grew up in DOS, and I've been working nonstop in computers since the mid-80's.  I even studied Unix in college.  But despite all that, my terminal skills are embarrassingly limited.  I can get around directories, but my working knowledge of terminal commands is not very broad.  (Oh, the shame!  :()

Quickly, I've got an AMD Athlon XP 1500+ with (2) 512 sticks of SDRAM.  Here is the "dmidecode" for my current setup, with MAY more information than necessary:

```
# dmidecode 2.9
SMBIOS 2.2 present.
36 structures occupying 946 bytes.
Table at 0x000F0800.

Handle 0x0000, DMI type 0, 19 bytes
BIOS Information
	Vendor: Phoenix Technologies, LTD
	Version: 6.00 PG
	Release Date: 04/01/2002
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 256 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		AGP is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
	Manufacturer: VIA Technologies, Inc.
	Product Name: VT8367-8233A
	Version:  
	Serial Number:  
	UUID: Not Present
	Wake-up Type: Power Switch

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer:  
	Product Name: VT8367-8233A
	Version:  
	Serial Number:  

Handle 0x0003, DMI type 3, 13 bytes
Chassis Information
	Manufacturer:  
	Type: Desktop
	Lock: Not Present
	Version:  
	Serial Number:  
	Asset Tag:  
	Boot-up State: Unknown
	Power Supply State: Unknown
	Thermal State: Unknown
	Security Status: Unknown

Handle 0x0004, DMI type 4, 32 bytes
Processor Information
	Socket Designation: Socket A
	Type: Central Processor
	Family: Duron
	Manufacturer: AMD
	ID: 62 06 00 00 FF F9 83 03
	Signature: Family 6, Model 6, Stepping 2
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
	Version: AMD Athlon(tm) XP
	Voltage: 3.3 V
	External Clock: 100 MHz
	Max Speed: 1500 MHz
	Current Speed: 1300 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0009
	L2 Cache Handle: 0x000A
	L3 Cache Handle: No L3 Cache

Handle 0x0005, DMI type 5, 22 bytes
Memory Controller Information
	Error Detecting Method: None
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: Four-way Interleave
	Maximum Memory Module Size: 32 MB
	Maximum Total Memory Size: 96 MB
	Supported Speeds:
		70 ns
		60 ns
	Supported Memory Types:
		Standard
		EDO
	Memory Module Voltage: 5.0 V
	Associated Memory Slots: 3
		0x0006
		0x0007
		0x0008
	Enabled Error Correcting Capabilities: None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A0
	Bank Connections: 0 1
	Current Speed: 60 ns
	Type: Other SDRAM
	Installed Size: 512 MB (Double-bank Connection)
	Enabled Size: 512 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A1
	Bank Connections: 2 3
	Current Speed: 60 ns
	Type: Other SDRAM
	Installed Size: 512 MB (Double-bank Connection)
	Enabled Size: 512 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A2
	Bank Connections: None
	Current Speed: 60 ns
	Type: Unknown
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x0009, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Internal Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 128 KB
	Maximum Size: 128 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x000A, DMI type 7, 19 bytes
Cache Information
	Socket Designation: External Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: External
	Installed Size: 256 KB
	Maximum Size: 256 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PRIMARY IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SECONDARY IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: FDD
	Internal Connector Type: On Board Floppy
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: 8251 FIFO Compatible

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: COM1
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator:  
	External Connector Type: DB-9 male
	Port Type: Serial Port 16450 Compatible

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: COM2
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator:  
	External Connector Type: DB-9 male
	Port Type: Serial Port 16450 Compatible

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: LPT1
	Internal Connector Type: DB-25 female
	External Reference Designator:  
	External Connector Type: DB-25 female
	Port Type: Parallel Port ECP/EPP

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Keyboard
	Internal Connector Type: PS/2
	External Reference Designator:  
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PS/2 Mouse
	Internal Connector Type: PS/2
	External Reference Designator:  
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Other
	Port Type: USB

Handle 0x0014, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI0
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 1
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0015, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI1
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 2
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0016, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI2
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 3
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0017, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI3
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 4
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0018, DMI type 9, 13 bytes
System Slot Information
	Designation: AGP
	Type: 32-bit AGP
	Current Usage: Available
	Length: Long
	ID: 8
	Characteristics:
		5.0 V is provided

Handle 0x0019, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 3
		n|US|iso8859-1
		n|US|iso8859-1
		r|CA|iso8859-1
	Currently Installed Language: n|US|iso8859-1

Handle 0x001A, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 768 MB
	Error Information Handle: Not Provided
	Number Of Devices: 3

Handle 0x001B, DMI type 17, 21 bytes
Memory Device
	Array Handle: 0x001A
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: A0
	Bank Locator: Bank0/1
	Type: Unknown
	Type Detail: None

Handle 0x001C, DMI type 17, 21 bytes
Memory Device
	Array Handle: 0x001A
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: A1
	Bank Locator: Bank2/3
	Type: Unknown
	Type Detail: None

Handle 0x001D, DMI type 17, 21 bytes
Memory Device
	Array Handle: 0x001A
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: A2
	Bank Locator: Bank4/5
	Type: Unknown
	Type Detail: None

Handle 0x001E, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 1 GB
	Physical Array Handle: 0x001A
	Partition Width: 0

Handle 0x001F, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0001FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x001B
	Memory Array Mapped Address Handle: 0x001E
	Partition Row Position: 1

Handle 0x0020, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00020000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x001C
	Memory Array Mapped Address Handle: 0x001E
	Partition Row Position: 1

Handle 0x0021, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x001D
	Memory Array Mapped Address Handle: 0x001E
	Partition Row Position: 1

Handle 0x0022, DMI type 32, 11 bytes
System Boot Information
	Status: No errors detected

Handle 0x0023, DMI type 127, 4 bytes
End Of Table

```

---

### Post by hyper_ch on 2009-03-28
looks fine to me this far. Go into recovery mode and then move your current home folder /home/username to something else like /home/backup and then try to login graphially again.

---

### Post by OlPeculiar on 2009-03-28
I will try that.  I am off to a basketball game right now, but I'll get working on this as soon as I'm able.  Please keep any other suggestions coming, and keep an eye open for my next reply.  Thanks again!

 - OlPeculiar

---

### Post by OlPeculiar on 2009-03-29
Ah - good game.

Okay, I went into recovery mode, dropped to the command line, went into the home folder and issued the "mv" command:

```
mv my_profile_name backup
```

The "ls" command confirmed that the directory had been reassigned to "backup".  I then tried the GUI login screen again.  But it still locks up, exactly the same way that it did before.

Actually, "locks up" isn't the proper term, because the mouse still moves the pointer, and the keyboard LEDs still respond.  So the entire system isn't locked - it's just that the GUI immediately stops responding, usually right after I type in my user name.

The only new hardware in the machine is the Adaptec 2610SA and the Caviars that it is controlling - I'd hate to have to give up Ubuntu or the hardware due to lack of compatibility.  I'm going to look into flashing the RAID card - perhaps an update might help?

 - OlPeculiar

---

### Post by hyper_ch on 2009-03-29
go again to the recovery shell and check if the new home folder for your user was created. maybe you need to create it manually.

---

### Post by OlPeculiar on 2009-03-30
I went back in through the recovery shell, and a new folder had indeed been created for my username.

I've also enlisted the help of a buddy of mine, who has a lot more Ubuntu install experience than I have.  He considered that perhaps the GRUB needed to be replaced by hand.  He directed me to this page:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I tried it, but it didn't help - the lockup was exactly the same.

I considered the possibility that the raid array was too large, possibly exceeding the 2TB limit that so many controllers have, and perhaps that was causing problems.  The logical drive was actually only 1.8TB, so this was real long shot, but I tried it anyway.  I abandoned the existing RAID 5 array in favor of a RAID 1 array using two drives - no warning about any 2TB limit when I created the array, so that was a good sign.  I reinstalled Ubuntu again, without any issues, but the login screen still locked up, the same way it had before.  So we know it's not the raid array.  I'm currently rebuilding the RAID 5 array...

Right now, we're looking at the graphics driver.  We have both found some forum discussions that match my symptoms pretty well.  So, once I get back to my computer, I'm going to reinstall Ubuntu (fully expecting it to lockup at login), and then we'll start experimenting by swapping out video cards or video drivers.  If we can get Ubuntu to work by swapping out the video card, then that will pinpoint the problem.  And then we can start working on getting Ubuntu to play with my real video card by using different drivers.

So that's our plan.  I eagerly welcome any comments or suggestions.  Otherwise, I'll keep this thread updated - hopefully others can benefit from what I'm learning...

 - OlPeculiar

---

### Post by hyper_ch on 2009-03-30
the first login (hence creating a new skeleting profile) usually takes a bit longer... so it's still locked?

---

### Post by OlPeculiar on 2009-03-30
That's a good question.  I did give it a few minutes to respond, but it's not like I walked away for 20 minutes or anything like that.  I came to the conclusion that it was truly locking up because: 

A) it becomes completely unresponsive after I enter my username but before I enter the password; 
B) after becoming unresponsive I cannot click on the "options" button in the lower left corner;
C) even clicking the "options" button ***before*** entering my username will cause it to become unresponsive.  

But, when I reinstall again, I will try giving it an extra long time to respond.  (Boy, will I feel silly if it's something as simple as that!)  I'll also keep an eye on the raid controller LEDs, to determine if there's any activity there.

 - OlPeculiar

---

### Post by hyper_ch on 2009-03-30
well, that's too long.... and it should become unresponsive after you enter the username. Something's not good there. Drop again to rescue root shell and run

on ubuntu:
```

sudo apt-get purge gdm && sudo apt-get install gdm

```

on kubuntu:
```

sudo apt-get purge kdm && sudo apt-get install kdm

```

---

### Post by OlPeculiar on 2009-03-30
I will try that, the next time that I am able.  (I'm going to be away from my computer for the next couple days, so it might be a while before you hear any results.)

But what exactly will this code do?  It basically purges and then reinstalls the graphical login window, yeah?

 - OlPeculiar

---

### Post by hyper_ch on 2009-03-30
yes, that's what it should do. you might need to setup to ethernet for the install to work as you very likely don't have a .deb downloaded yet for gdm/kdm

---

### Post by OlPeculiar on 2009-03-31
Because I had rebuilt the RAID 5 array, I had to do another reinstall.  So I haven't tried the "apt-get purge" code that you suggested - not yet anyway.  For the first login of this new install, I did a <ctrl><alt><F2> to drop down to text-based login - I was hoping the problem might be a graphics driver...

After I entered my username, it locked up again!  But this time, it generated some messages after about a minute or so.  I tried to write it down, but I didn't get very much down before the whole screen filled with more information.  The first line of information began with:

> 99.608053] aacraid:Host

That's all I wrote down before it got scrolled off the top of the screen.  But down at the bottom, I noted this:

> scsi appears hung

So whatever this problem is, it appears to be the scsi card.  Would Ubuntu report the 2610SA SATA RAID card as a scsi device?

I'm going to google the phrase "scsi appears hung" to see what I can find.  I'll also try the "apt-get purge" idea you suggested.

That's the news, weather and sports for now - more news as it breaks...

 - OlPeculiar

---

### Post by RayRuest on 2009-03-31
Can you read/write to the RAID5 partition when booting from the Live disk?  If so we can at least confirm that Ubuntu is OK with the controller.

---

### Post by OlPeculiar on 2009-03-31
I meant to include that in the last post.  I can open the HD volume and look at the contents - and the RAID controller LEDs flash appropriately.  

But I cannot create a new document anywhere within that volume, and I cannot copy/paste anything to it.  It's almost like the thing is "read only".

I'm going to try the text login through recovery mode now...

 - OlPeculiar

---

### Post by OlPeculiar on 2009-03-31
Back again, in LiveCD.

I restarted and dropped into recovery mode.  Dropped to a command line, typed "login", and successfully entered both username and password to login at the command line.  

I then tested the raid array by creating two random directories using "sudo mkdir".  The directories were created without incident.

Back into the LiveCD, I opened the raid-5 volume and confirmed - the two directories I created are still there.  But I still cannot modify any of the contents of the raid-5 volume.

I checked the disk properties, and went to the permissions tab:  

Owner: root
Folder access:  (grayed out)
Group: root
Folder access:  (grayed out)
Others
Folder access:  (grayed out)
Execute:  (grayed out)
SELinux context: unknown
Last changed: unknown

"You are not the owner, so you cannot change these permissions."


I have no idea if any of that is relevant, but there it is anyway.

Any thoughts?

 - OlPeculiar

---

### Post by OlPeculiar on 2009-04-10
Sorry I've been away for so long, but I'm up and running!  Running Jaunty, actually, but moving up to 9.04 instead of struggling with the 8.1 install was not what solved the problem...

I ran the install for 9.04 from the alternate install disk, to see if that would solve the problem.  It didn't - I got a successful install, but the OS still locked up at the login screen, immediately after entering my username.

Days pass...

I went to flash the firmware on the 2610SA controller, hoping that might help, but a long time ago I had disconnected my floppy drive - really, who needs those anymore?  So I went into the computer case to reconnect the floppy, and while I was in there, I pulled the old 56k modem that had been sitting idle for - well, a really long time.  I don't think that modem ever had a chance to experience the Y2K bug, if you get my drift.  Anyway...

The controller flash didn't take because the vendor codes between the firmware and the hardware didn't match.  As the machine was restarting from that process, Jaunty started to boot and I just let it go - you don't want to shut down in the middle of a boot process.  So it got to the login screen, I typed my username, and then I pressed the first character in my password - and it worked.  I typed the second character, and then the entire password, and I was in!  

As I'm sure you've surmised, it was the modem.  See, I used to know better than this:  Hardware conflicts are a prime source of problems, and it should have been one of the first things I checked.  Pull out or disable anything you're not using, and if that doesn't work, then pull out everything you ARE using, and add things back in one by one until the machine crashes again.  That's a standard diagnostic technique, and those simple steps cost me a lot of time and aggravation.

I experienced a couple different symptoms throughout this process - or at least, symptoms that presented in several different ways.  And I can't say that my solution will help everybody that experiences the same problems.  But hopefully my two week struggle will help others.  Swap hardware!  Pull anything you're not using!  And above all - don't be afraid to sound like an idiot!  I do it all the time.  But at least I'm up and running.

Cheers, and thanks very much to all who helped!

 - OlPeculiar.

---

### Post by OlPeculiar on 2009-05-03
I'm back with essentially the same problem - it reappeared after the upgrade from 9.04 beta to the full version.  I detailed it in the following thread, and it occured to me that I should include it here as well...

[http://ubuntuforums.org/showthread.php?t=1144565](http://ubuntuforums.org/showthread.php?t=1144565)

Any thoughts, anybody?

 - OlPeculiar

---

