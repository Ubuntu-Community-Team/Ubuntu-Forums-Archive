---
title: "fresh install 10.4 will not boot"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by modelmaker on 2010-07-03
I'm a long-time OSX user, attempting to become familiar with Ubuntu. After three attempts to install on two different Macs, I'm unable to arrive at a bootable Ubuntu. Here's scenario #3:

1. Using Apple's Disk Utility, a new 500 GB hard drive was installed in a 2007 Intel Mac mini, overwritten with zeros and partitioned to create one 270 GB volume for OSX; remaining space left empty for Ubuntu system and swap.

2. OSX 10.6.3 was installed uneventfully.

3. Ubuntu 10-4 was downloaded and burned to create a bootable CD.

4. rEFIt was downloaded and installed on the OSX volume.

5. Terminal was used to enable rEFIt:
	cd /efi/refit
	./enable-always.sh

6. rEFIt and OSX both tested OK. 

7. Ubuntu booted from the CD OK and was used to install into the empty space. Option selected was simply to install; no manual sizing of partitions. No errors or odd behavior noted.

8. At the end of the installation, an unending stream of errors appeared on screen: "I/O error , dev sr0, sector nnnn"  (nnnn incrementing unendingly)

9. Mac was shut down and rebooted.

10. Upon appearance of rEFI screen, Partitioning Tool was selected to update MBR to agree with GPT. 

	No opportunity to execute MBR update occurred. Instead an error notice advised:
	
	"Status: MBR Partition Table is invalid, partitions overlap"
	"Error: 'not found' returned from gptsync.efi"
	
GPT and MBR table extents were displayed 

	Current GPT partition table:
	#   Start LBA		   End LBA         Type
	1		  40			409639		EFI system
	2     409640		   568137503	Mac OSX
	3    568137728       568139775      Grub 2 Bios Port
	4    568139776       960120831      Basic Data
	5    960120832       976773119      Linux Swap
	
	Current MBR Partition Table:
	# A Start LBA         End LBA          Type
	1                  1         409639            EE EFI Protective
	2       409640      568137503      AF Mac OSX HFS+
	3                  1      568139775       EE EFI Protective
	4    568139776  960120831       83 Linux
	
=> Q: Looks like I need to erase and start over. If so, what should I do differently on the 4th try?

NB: 
	I was unable to manually define Ubuntu volume extents. After defining the system volume, Ubuntu insisted there was '0' space remaining for swap, regardless of how much the system volume was decreased in size. So the default was selected.
	
	Near the end of installation, bootloader and grub were installed and grub was updated.

Thanks for any advice --
-- Modeler

---

### Post by -humanaut- on 2010-07-03
I'm not familiar with macs at all but I believe you need something called bootcamp I'm really not sure its an x86 intel mac right? if its a PPC then you need to set_env but I don't remember how or how well Lucid is supported on the PPC platform.

---

### Post by lkjoel on 2010-07-03
go here:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
then check screenshot.png.

For those Ubuntu-savy users, you might notice I'm running puppylinux.
I will be back to my Ubuntu desktop on August 1st.

---

