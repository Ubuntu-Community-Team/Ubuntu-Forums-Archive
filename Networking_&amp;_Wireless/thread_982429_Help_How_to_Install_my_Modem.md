---
title: "Help How to Install my Modem"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by NightRock on 2008-11-14
Im new Ubuntu user please help how to install my Modem, Im currently using HP dv2197 it has a build in modem, I need to use it for dial up connections.

---

### Post by cruising on 2008-11-14
> **NightRock said:**
> Im new Ubuntu user please help how to install my Modem, Im currently using HP dv2197 it has a build in modem, I need to use it for dial up connections.

And yes, I have the same problem. My machine is Toshiba Satellite A25 S207, P4, 2.66GHZ, 512MB. I somehow managed to get the ModemData.txt result following info online. But going further just proved to be too 'text-based', at least until I really join the group. It's a general problem and my screen ain't full either. Somebody help!

Thanks!

---

### Post by cruising on 2008-11-17
Hello!
I just finished installing Ubuntu 8.04 LTS on a Toshiba Satellite A25 S270, P4, 512MB RAM, 2.66GHZ, 17" screen. The install went smoothly only to get me stuck on this great issue:

I live in a place where dial up rules with the "World Wide Wait" motto! And so I always use my modem in Windows to connect to the internet, but don't seem to find a way to do it in Ubuntu. I got to using ScanModem to detect my modem and I got a text file with lots of things in it; Here it is:

================================================
 Only plain text email is forwarded by the <email address hidden> List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry kernel 2.6.24-19-generic
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from <email address hidden> are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org)
-------------------------- System information ----------------------------
CPU=i686,
Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008
 scanModem update of: 2008_11_06

 There are no blacklisted modem drivers in /etc/modprobe* files
Attached USB devices are:
 ID 0930:6545 Toshiba Corp.

USB modems not recognized

For candidate card in slot 00:09.0, firmware information and bootup diagnostics are:
 PCI slot PCI ID SubsystemID Name
 ---------- --------- --------- --------------
 00:09.0 10b9:5457 1179:0001 Modem: ALi Corporation M5457 AC'97 Modem Controller

 Modem interrupt assignment and sharing:
 11: 7170 XT-PIC-XT ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3, yenta, yenta, ALI 5451, pcmcia0.0, eth0
 --- Bootup diagnostics for card in PCI slot 00:09.0 ----
[ 1360.701413] PCI: Enabling device 0000:00:09.0 (0000 -> 0003)
[ 1360.701779] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKI] -> GSI 11 (level, low) -> IRQ 11
[ 1360.701790] ACPI: PCI interrupt for device 0000:00:09.0 disabled

 The PCI slot 00:09.0 of the modem card may be disabled early in
 a bootup process, but then enabled later. If modem drivers load
 but the modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to <email address hidden>
 if help is needed.

For candidate card in slot 00:06.0, firmware information and bootup diagnostics are:
 PCI slot PCI ID SubsystemID Name
 ---------- --------- --------- --------------
 00:06.0 10b9:5451 1179:0221 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device

 Modem interrupt assignment and sharing:
 11: 7174 XT-PIC-XT ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3, yenta, yenta, ALI 5451, pcmcia0.0, eth0
 --- Bootup diagnostics for card in PCI slot 00:06.0 ----
[ 1381.348911] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
[ 1381.349208] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11

============================================================

If you've been through this, you will understand the mix of the love you have for Ubuntu and the 'despicableness' of the being cut away from the rest of the world while you have the best OS in your machine?!@$#&$?!! So, please have some compassion, will ya? 

Thanks,

Cruising


EDIT: Maturity takes time! :) That's what I've learned from my experience with Ubuntu. It could really shock you at first ... but bit by bit you will get by. And if you're good at finding info online, it shouldn't be a problem for you! The reason I'm adding this EDIT is because I just want to tell anyone in a similar situation to go to: [www.linmodems.org](www.linmodems.org) and you will find all the info you need there! 

Cheers!

---

