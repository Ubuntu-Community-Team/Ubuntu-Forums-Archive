---
title: "Problems installing Intel537EP modem"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by mcgrg6 on 2008-11-01
Hi, I am completely new to the Linux OS.  As a result of a hard drive failure on a relatives Dell Dimension 3000 I am taking the opportunity to try Ubuntu Hardy.  All goes well but I need to get the system to recognise & use my dial-up modem.  Oddly a wireless usb adapter (SAFECOM SWMULTZ) works fine connecting to my network - thats how I am sending this request.  I need the dial-up as the relative does not have wireless internet.

Anyway I ran the scanmodem (report below) and found the modem is the INTEL537EP.  I then downloaded    

intel537ep-hardy_2-Philippe.Vouters_i386.deb

and clicked on it and went through what looked like a loading process.  the message I got back in a file called success.txt was

Congratulations. If you are reading this file then your modem driver should be
installed properly. Remember to reboot with the proper kernel if the driver was
not able to be loaded.

-Quick Info

Your Modem should be accessible from both these locations:
   /dev/537
   /dev/modem

So that all looked positive but when I tried connecting with "Gnome PPP" the reply is cannot open modem.  I can find no way to get the system to dial up my isp.

So any help appreciated - but please note I am new to this OS and the ways of entering commands. I do know how to access the terminal and I have roamed around.    

Regards,
Mike

MODEMDATA.TXT report

--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008
 scanModem update of:  2008_10_24
The modem symbolic link is /dev/modem -> /dev/537
 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 0ace:1215 ZyDAS WLA-54L WiFi
 ID 058f:6387 Alcor Micro Corp. Transcend JetFlash 110 USB 2.0 Flash Drive (2GB)
 ID 413c:2010 Dell Computer Corp. 
 ID 413c:1003 Dell Computer Corp. 
 ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse

USB modems not recognized

For candidate card in slot 01:01.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 01:01.0	8086:1080	1028:1000	Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI 

 Modem interrupt assignment and sharing: 
 --- Bootup diagnostics for card in PCI slot 01:01.0 ----
[   23.314637] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 22 (level, low) -> IRQ 16
[   23.315027] 0000:01:01.0: ttyS1 at I/O 0xde08 (irq = 16) is a 16450
[   23.315257] 0000:01:01.0: ttyS2 at I/O 0xde10 (irq = 16) is a 8250
[   23.315468] 0000:01:01.0: ttyS3 at I/O 0xde18 (irq = 16) is a 16450
[   23.315536] Couldn't register serial port 0000:01:01.0: -28

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 01:01.0:
	Modem chipset  detected on
NAME="Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI "
CLASS=0703
PCIDEV=8086:1080
SUBSYS=1028:1000
IRQ=16
IDENT=INTEL537EP

 For candidate modem in:  01:01.0
   0703 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI 
      Primary device ID:  8086:1080
 Support type needed or chipset:	INTEL537EP
 

----------------end Softmodem section --------------

---

