---
title: "Need help updating my BIOS"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by jacatone on 2009-03-10
I'm running Ubuntu 8.10 on an old AMD Duron white box that's been sitting in a closet for several years. I'd like to try updating the BIOS. The info on the BIOS is as follows:

jacatone@eMax ~ $ sudo dmidecode --type 0
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: Award Software International, Inc.
	Version: 6.00 PG
	Release Date: 09/06/2000
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


What information should I be looking for to download the update? Thanks.

---

### Post by avtolle on 2009-03-10
I don't know if this will help you, but take a look at [http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789) for some information and potential answers.

---

### Post by issih on 2009-03-10
You want to find the exact make and model of your motherboard...then go to the manufacturers website and download the latest bios for that motherboard.

---

### Post by abn91c on 2009-03-10
Open the computer, unplug Power, get flash light and look for the model number on the board, I had an old 1000mhz MB and the number was near the PSU plug.Make sure you get the exact number, a bad flash will turn the motherboard into a paperweight

---

### Post by louieb on 2009-03-10
BIOS is customized to each mother board model . What I do is look on the board and find the model ID. Put the model ID into Google and see what pops up.   Good Luck.

---

