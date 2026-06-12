---
title: "eth0 issues"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by jayman76 on 2007-06-01
Been searching on the forums and can't seem find, or rather, can't seem to word my search to find a solution.... my wireless is working fine and is marked as eth1. I want to use eth0 NIC to connect to my corporate network but I can't get it up.

#/etc/network/interfaces shows it should be up:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid NYPL



#sudo ifup eth0 fails
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.


# and the NIC shows in lscpi:
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller

Not sure what else to try....

-Jay

---

### Post by dmizer on 2007-06-02
you sure your gb card is eth0?

i have no idea why this is the case, but when using multiple network adapters, ubuntu likes to lie about the number.  first, check dmesg to make sure that ubuntu is even loading a module for your card.  double check to make sure that ubuntu calls it eth0 in dmesg.

if your card does indeed have a module loading for it, just try changing eth0 to eth2 or eth3 to see if you get a hit.

---

### Post by bukwirm on 2007-06-02
Try the command "sudo lshw -C network" - it should show you the logical name of all the networking devices.

---

### Post by jayman76 on 2007-06-02
Thanks for the help. 

lshw show's the NIC.

Info in dmesg shows a problem loading the module. Not sure what to do about it (searching google).  

[    3.704000] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[    3.704000] Copyright (c) 1999-2006 Intel Corporation.
[    3.704000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ
 20
[    3.704000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    3.760000] usbcore: registered new interface driver usbfs
[    3.760000] usbcore: registered new interface driver hub
[    3.760000] usbcore: registered new device driver usb
[    3.760000] USB Universal Host Controller Interface driver v3.0
[    3.764000] SCSI subsystem initialized
[    3.788000] libata version 2.20 loaded.
[    3.796000] e1000: 0000:02:00.0: e1000_probe: The EEPROM Checksum Is Not Vali
d
[    3.816000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[    3.824000] e1000: probe of 0000:02:00.0 failed with error -5
[    3.840000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ
 20


Any suggestions?

Thanks again!

---

### Post by kevdog on 2007-06-02
What are the contents of your /etc/iftab file??

---

### Post by jayman76 on 2007-06-02
Content of iftab are:

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:d3:31:58:57 arp 1
eth1 mac 00:18:de:63:cd:2d arp 1



I did find this: [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-67166](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-67166)

Looked very promising, then I ran the script and it screamed back: eth0: error fetching interface information: Device not found

Trying to run a script on device the system won't load in the first place :confused:

There are some other potential workarounds listed at [http://www.thinkwiki.org/wiki/Problem_with_e1000:_EEPROM_Checksum_Is_Not_Valid](http://www.thinkwiki.org/wiki/Problem_with_e1000:_EEPROM_Checksum_Is_Not_Valid) a poster mentions ubuntu but no solution.

Thanks!

---

### Post by jayman76 on 2007-06-02
So, following the recommendations from thinkwiki plugging in a cable didn't work, adding and removing the module did nothing, disabling and enabling the nic in the bios did work... for now. If it messes up, I'll update the post.

---

### Post by jayman76 on 2007-06-02
disabling and enabling the nic in bios lasted one reboot :(
back to the drawing board.

---

