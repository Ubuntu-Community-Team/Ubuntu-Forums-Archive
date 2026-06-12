---
title: "Very slow from smb share (to 7.04) but to 7.10 OK"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by candtalan on 2007-12-14
For the record:
I am recently using a network attached storage (NAS) unit on a wired LAN. The NAS unit has a SMB server, also a FTP server, and also a USB2 connector. Everything works ok (separately)  - except for traffic *from* the NAS to my (kubuntu) 7.04
Package smbfs is installed.

Writing to the NAS (smb) is fine, I get about 3MB/s indicated. However, from the NAS, say, copying a CD iso file from the NAS to my kubuntu machine, is remarkably slow, typically around 100kb/s, or even less, 30 is often seen. This is useless of course. The same happens with ubuntu (7.04) which I have as an alternative desktop environment on this install. This happens even when two files are pasted at the same time, if that makes any difference.

However, also on this machine, I have kubuntu 7.10 as a separate install, and this smb speed problem does not occur. 
I have seen some threads about slow samba shares, including with a suggestion it may have a possible relationship with the network card hardware or driver. In this machine I am using the onboard NIC facility.

My experiments also included using another machine nearby,  which is dual boot xp and kubuntu 7.10. The transfer from the NAS to the machine is 3MB/sec. Also using xp, similar.

I guess that either my mounting of the share is somehow a problem (cannot see what though?) or the NIC used is handled better in 7.10 than in 7.04.

Main board is: ASUS P4C800 (RAM is 1GB)

lspci output:
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
02:0b.0 Communication controller: Intel Corporation 536EP Data Fax Modem

fstab line:
#Mount of Network attached storage box
//192.168.1.42/store1 /home/user1/NAS-mnt smbfs uid=1000,umask=000,user,rw   0      0

NAS unit: Mobile LANDISK External Net Storage (from Maplin UK) uses my own hard drive fitted.

Conclusion:
I am pretty well happy to move to 7.10 anyway, and with my wish for the NAS I will, but I am mystified about why 7.04 gives me such slow (smb) speed.

---

