---
title: "Is there a problem USB PCI Card in Dapper??"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by Robroy11976 on 2006-07-20
Hi ... i just installed Dapper 6.06 and my USB2.0 PCI Card cannot read the flash disk i inserted or any device for that matter .... Is there an issue with that?

---

### Post by az on 2006-07-20
No, there is no issue with that - they work fine.

Post the output of

dmesg

from a terminal.

---

### Post by Robroy11976 on 2006-07-20
So you mean if i type "dmesg" it will just work after that???  My 256mb flash drive won't detect, as well as my other device .... But when i check on the device manager ... not sure but the way i see it ... it seems the usb2.0 controller is there ....

---

### Post by Robroy11976 on 2006-07-20
What i mean to say that it can't detect my flash drive is that .. when i insert it, nothing happens ... no activity whatsoever like i wasn't there ...

---

### Post by az on 2006-07-20
Yes.  I understand.  Running that command shows all the hardware detection that happens when you boot your computer.  That will reveal if your pci usb card is being detected or not, or if there is an obvious problem.


Just run
dmesg
in a terminal, cut, paste and post the output to a message.


Also, run

tail -f /var/log/messages

in a terminal and then plug in a device that doesn't work.  Post the output of that, too.  You should see some messages appear when your computer detects the device.  It should take less than two seconds or so.

---

### Post by Robroy11976 on 2006-07-20
OK .. i'll try to run it again later and post it here ... still have setup a 20meters of CAT5 cable to reach my desktop so i could copy the output... that's why i want to setup the usb 2.0 card in order for my wireless usb to get connected :)

---

### Post by Robroy11976 on 2006-07-21
Here it is ... i copied/paste from the terminal the output i think related to my usb pci card using the "dmesg" command.  And i guess this is it, 4 ports detected ...

[4294678.435000] hub 5-0:1.0: USB hub found
[4294678.435000] hub 5-0:1.0: 4 ports detected
[4294678.562000] Probing IDE interface ide1...
[4294679.081000] Probing IDE interface ide2...
[4294679.600000] Probing IDE interface ide3...
[4294680.231000] Attempting manual resume
[4294680.293000] EXT3-fs: mounted filesystem with ordered data mode.
[4294680.322000] kjournald starting.  Commit interval 5 seconds
[4294697.944000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294697.953000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294697.990000] Linux agpgart interface v0.101 (c) Dave Jones
[4294698.000000] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[4294698.010000] agpgart: AGP aperture is 128M @ 0xd0000000
[4294698.201000] 8139too Fast Ethernet driver 0.9.27
[4294698.201000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5


And this is the text output when i run "tail -f /var/log/messages" and inserted my usb flash drive ....


Jul 20 18:52:15 robroy-desktop gconfd (root-5296): Exiting
Jul 20 19:05:43 robroy-desktop kernel: [4296325.492000] usb 5-2: new high speed USB device using ehci_hcd and address 2
Jul 20 19:06:02 robroy-desktop kernel: [4296344.000000] usb 5-2: new high speed USB device using ehci_hcd and address 3
Jul 20 19:06:20 robroy-desktop kernel: [4296362.508000] usb 5-2: new high speed USB device using ehci_hcd and address 4
Jul 20 19:06:31 robroy-desktop kernel: [4296373.012000] usb 5-2: new high speed USB device using ehci_hcd and address 5


It just stopped right there and from the looks of it, it did detect my drive .... so how come it doesn't appear as another drive or something ????

---

### Post by Robroy11976 on 2006-07-22
Where do you think is the prob???

---

### Post by az on 2006-07-22
> **Robroy11976 said:**
> 
Jul 20 19:05:43 robroy-desktop kernel: [4296325.492000] usb 5-2: new high speed USB device using ehci_hcd and address 2



ehci is usb2.  Do the decives work using other usb ports (usb1.1)?

Do they work on other machines running ubuntu?

Are you using a hub?

---

### Post by Robroy11976 on 2006-07-22
My flash disk do work if i insert it in the usb1.1 slot which is built-in to my motherboard .... The device i install is the usb2.0 4 port pci card ... i think it did detected when i insert the flash disk, but the log messages just stopped there... Then nothing happens, it does mount ...

---

### Post by az on 2006-07-22
Ar eyou sure it is not defective?  If the pci card works in windows, for example, this is a bug.  You must report it.

I looked and cannot find a similar bug.
[https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=usb2&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=usb2&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)


I would suggest yoiu file it under the linux-source package.  Name it something like

"usb2 pci card does not work- device works when inserted into usb1.1 slot but not into usb2 slot on pci card"

The give the details about your problem and the commands and outputs you posted here.

Within a short while, you may be asked for more details (you will be told to run commands and post their outputs.)  Please follow up on this bug.

Feel free to ask any other questions about reporting this bug.  I would say it is pretty important to report it.

---

### Post by Robroy11976 on 2006-07-22
Thanks for the Help ... will do that :)

---

### Post by az on 2006-07-23
Please post the bug report number...

---

### Post by Robroy11976 on 2006-07-23
Bug #53784

---

