---
title: "Do not find Sw Modem in laptop"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by Eskild69 on 2008-05-15
Hi,
I am a newbe in Linux, but I have installed Ubuntu 8.04 on my Toshiba x200. It has a inbuilt modem, but Ubuntu will not find any modems.
I have used Modemdata, and below you find the txt.
Pls help me find what modem / chipset I have so I can find a linux driver for my modem.

 		 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-16-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Your contry's local Linux experts
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html). 
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008
 scanModem update of:  2008_05_02

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 04f2:b008 Chicony Electronics Co., Ltd 
 ID 1532:0007  
 ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader

USB modems not recognized
For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:284b	1179:ff00	Audio device: Intel Corporation 82801H 

 Modem interrupt assignment and sharing: 
 22:        408        395   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   33.910819] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   33.910841] PCI: Setting latency timer of device 0000:00:1b.0 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.
 PCI slot 00:1b.0 has a High Definition Audio Card

The ALSA verion is 1.0.15
The modem cards detected by "aplay -l"  are:


The /proc/asound/pcm file reports:
-----------------------
00-02: ALC268 Analog : ALC268 Analog : capture 1
00-01: ALC268 Digital : ALC268 Digital : playback 1
00-00: ALC268 Analog : ALC268 Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf7600000 irq 22
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 00:1b.0:
	Modem chipset  detected on
CLASS="Class 0403: 8086:284b"
NAME="Audio device: Intel Corporation 82801H "
SUBSYS=1179:ff00
PCIDEV=8086:284b
IRQ=22
HDA=8086:284b
SOFT=8086:284b.HDA
CodecArchived=11c11040
ArchivedChip=0x11c11040
IDENT=11c11040_Not_supported.

 For candidate modem in:  00:1b.0
   Class 0403: 8086:284b Audio device: Intel Corporation 82801H 
      Primary device ID:  8086:284b
    Subsystem PCI_id  1179:ff00 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 0x11c11040, residing on 1179:ff00 lacks support from LSI/Agere.
                        
      

Support type needed or chipset:	11c11040_Not_supported.

Read InfoGeneral.txt about alternative hardware

---

### Post by Eskild69 on 2008-05-21
Anyone, pls help me get online
Thanks

---

