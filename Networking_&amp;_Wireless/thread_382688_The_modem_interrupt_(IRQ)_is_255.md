---
title: "The modem interrupt (IRQ) is 255"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by Farooq3k on 2007-03-12
Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-10-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
 scanModem update of:  2007_Feb_21


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:0c.0	e159:0001	8086:0003	Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface

 Modem interrupt assignment and sharing: 

 --- Bootup diagnositcs for card in PCI slot 00:0c.0 ----

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

===================================
 The modem interrupt (IRQ) is 255 . IRQs of 0 or 255 are not functional!! 
 The CPU cannot control the modem until this situation is corrected!!
 Possible corrections are:
   1) Within the boot up BIOS, change from a Windows to a non-PNP/Other Operating System type.
   Instructions for accessing BIOS are at:
      [http://linmodems.technion.ac.il/resources.html](http://linmodems.technion.ac.il/resources.html) within:  Additional Resourcces.
   2a) Add an option "pci=routeirq" to the kernel boot up line.
      Here is an example paragraph from  /boot/grub/menu.lst :
	title           Ubuntu, kernel 2.6.15-26-686
	root            (hd0,6)
	kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hda7 ro pci=routeirq
	initrd          /boot/initrd.img-2.6.15-26-686
	savedefault
   2b) Same as above, but use "pollirq" instead of "pci=routeirq". 
   3) Within some BIOS setups, IRQ assignments can be changed.
   4) On non-laptop systems, moving the modem card to another slot has helped.
   5) Sometimes upgrading the kernel changes IRQ assignment.
=====================================

 For candidate modem in PCI bus:  00:0c.0
   Class 0780: e159:0001 Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
      Primary PCI_id  e159:0001
 Support type needed or chipset:	INTEL537
 


 Vendor e159 is Tiger Jet , [http://www.tjnet.com/](http://www.tjnet.com/)
  Controller e159:0001  translates PCI commands to the serial link used by
     the silabs DAA from the si3034, si3044 and si3056 family.
  The e159:0001  with SubSystem 8086:0003 is TJ320 v2.0 
  is the first and still most common of the Intel537 modem family.
  However primary controller chip can have broader uses:  [http://www.tjnet.com/chips/tiger320.htm](http://www.tjnet.com/chips/tiger320.htm)
  Though having its own driver package under 2.4.n. kernels,
  support (if any) from Intel is now included within the Intel-537EP package.

 ===

---

### Post by chili555 on 2007-03-12
And what happened when you: ```
Add an option "pci=routeirq" to the kernel boot up line.
Here is an example paragraph from /boot/grub/menu.lst :
title Ubuntu, kernel 2.6.15-26-686
root (hd0,6)
kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/hda7 ro pci=routeirq
initrd /boot/initrd.img-2.6.15-26-686
```

You can edit the boot parameters temporarily by pressing ESC at the prompt while booting up. Your exact details, kernel, etc. will be different, but you want pci=routeirq in there. Try it and let us know.

---

