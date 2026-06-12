---
title: "Create A USB Startup Disc - My Stick Is Now Broken"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by george1984 on 2009-01-29
Hello all.

	I used Intrepid to install a Hardy iso cd on to a Corsair Flash Voyager 8Gb.

	The reboot stalled with error messages scrolling down the screen typically being  of the form
"buffer I/O error on device fd0, logical block 0". Only way to stop this was to cut the power.
	Now the Voyager refuses to mount.

	Try sudo fdisk -l...Voyager is not listed

	Run Gparted...Voyager is not listed....the following appears in the terminal :-
	

	libparted : 1.7.1

======================

Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.

Input/output error during read on /dev/fd0

Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.

Input/output error during read on /dev/fd0


	Make inexpert attempt (I am primitive user)
 to mount this naughty Voyager...the following appears in terminal :-

sudo mount -t ext3 /dev/fd0 /media/temp

mount: block device /dev/fd0 is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/fd0,

       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try

       dmesg | tail  or so



george@MrGrumpy-01:~$ dmesg | tail

[17651.265006] end_request: I/O error, dev fd0, sector 0

[17663.426903] end_request: I/O error, dev fd0, sector 0

[17663.426910] Buffer I/O error on device fd0, logical block 0

[17675.596300] end_request: I/O error, dev fd0, sector 0

[17675.596307] Buffer I/O error on device fd0, logical block 0

[17687.749849] end_request: I/O error, dev fd0, sector 0

[17951.939874] end_request: I/O error, dev fd0, sector 0

[17964.109828] end_request: I/O error, dev fd0, sector 0

[17976.279091] end_request: I/O error, dev fd0, sector 2

[17976.279175] EXT3-fs: unable to read superblock


	Any ideas what I might try to return this stick to usefulness?

	corsairgt has posted in this forum that there is a batch of these Corsairs that are incompatible with Ubuntu. Do I now have a stick beyond redemption?

              PS...I could not work out how to place the code in a box. Senile decay. Probably.

---

### Post by Dedoimedo on 2009-01-29
fd is floppy disk - most likely not your usb device.
This kind of errors can stem from bad drivers, the disk being full. Can you try to mount it on another machine?
Dedoimedo

---

### Post by george1984 on 2009-01-29
Just tried it on an Asus P2 (different machine).

Same result, except Gparted terminal command curser continued to blink for several minutes before I closed the terminal.

If the Voyager is in place at boot then boot halts - frozen - not possible to enter bios or the boot menu.

For comparison I inserted a Dabs Value 4Gb (empty). Boot menu can be entered where it is correctely listed as an option. Booted the Dabs is mounted automatically as /media/disk.

Is it possible a kernel later than Intrepid is required for the Voyager?
Could there be a bios setting that might need changing?

---

### Post by cariboo on 2009-01-29
I would suggest trying [testdisk]("http:///www.cgsecurity.org/wiki/TestDisk") to see if you can recover your usb device. Testdisk is available in  the repositories.

If you don't need a floppy, or the computer you are booting doesn't have a floppy drive. Make sure it is disabled in the BIOS. If you get a message saying it can't find the floppy drive during boot up, just ignore it, as eventually it will time out.

Jim

---

### Post by george1984 on 2009-01-30
Hello again

                                                                       Asus A8N5X......

	Have entered the BIOS and disabled "Legacy Diskette A"
	In the Boot Settings Configuration there is "Boot up Floppy Seek" which is disabled (the handbook shows it as enabled)

	Installed and ran TestDisk. Insert Voyager. It apparently does not see the Voyager.

	Increasingly suspect (inexpertly) that the unsuccessful run of "Create a USB Startup Disk" has caused a bios recognition problem, or similar. I seem to remember that I did not drag the pointer quite all of the way to the right, which presumably would have left a small Fat32 partition on the stick. Does the machine think it is a floppy ( explaining that curious "fd"?).

	Reboot with Voyager still in place. Enter BIOS to investigate :-

Boot>Boot Device Priority>
		CDRom
		Hard Disk
		Legacy LAN
		Disabled

Boot>Hard Disk Drives
		Sata-M : Samsung
		Sata-M : WDC
		Corsair Flash Voyager 1.00
		Bootable Add-in Card

	Can the BIOS see the Voyager correctly? slightly confused.

	Exit the BIOS. Select Samsung hd in boot menu.The boot continues normally until the last few seconds when a screenful of text appears ending with :-
	"[94.598521] usb 5-4 : device descriptor read/64, error -110"
			    similar lines slowly scroll down screen.

	Booting with the voyager selected results in a blinking cursor and nothing else.

	Asus P2......

	There are no references to floppies. In USB Configuration there is "if Auto,USB devices less than 530Mb will be emulated as Floppy and remaining as hard drive. Forced FDD option can be used to force a HDD formatted drive to boot as FDD."	

	Bios recognition of the  Voyager is erratic. A cold start seems to be necessary. While it is recognised edit option to "FDD".

	Behavior of the Asus is almost the same as the other box.

			--------------------------------------------------------

	Did Intreped break the stick - is there a problem emerging: or is this bad hardware?

---

### Post by george1984 on 2009-01-31
Hello Again

Just tried the Voyager on an XP box. It was mounted and recognized ok.

    This seems to eliminate the bios as the culprit.

    Running "Create A USB Startup Disc" does seem to have broken the Voyager.

    Am I the first to report this problem?

---

### Post by george1984 on 2009-02-01
Hello again.

The explanation is to be found here

[http://www.houseofhelp.com/forums/showthread.php?t=71249](http://www.houseofhelp.com/forums/showthread.php?t=71249)

I have absolutely no windows knowledge, so completely zeroing the drive might be a problem.


I tried "Create a USB StartUp Disc" using a Dabs Value 4Gb drive. It also refused to boot with similar error messages. Fortunately, when reinserted Ubuntu could mount it, so I could wipe it and use it again as a simple storage device.

---

