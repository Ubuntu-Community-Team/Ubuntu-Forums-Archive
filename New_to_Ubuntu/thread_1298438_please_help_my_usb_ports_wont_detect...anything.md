---
title: "please help my usb ports wont detect...anything"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by fatzilla on 2009-10-22
A few days ago my usb ports just flat out stopped working on my laptop ( compaq presario V2000).  It happened shortly after upgrading to 9.04. Any device i plug in (flash drive, external HD, bluetooth adapter, etc) wont detect. i have been scouring the net to try and find a fix and the closest ive gotten was to run dmesg and this is what i get

(this is what caught my eye)
$ dmesg

[ 5428.732049] usb 1-1: new high speed USB device using ehci_hcd and address 15

[ 5428.837392] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5428.837406] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5429.041739] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5429.041797] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5429.245392] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5429.245403] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5429.449383] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5429.449391] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5429.653400] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5429.653408] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5429.653412] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?

[ 5429.709382] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5429.709389] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5429.913377] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5429.913384] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5430.117381] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5430.117390] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5430.321381] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5430.321388] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5430.525385] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5430.525392] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5430.525397] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?

[ 5430.581429] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5430.581436] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5430.785381] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5430.785388] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5430.989446] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5430.989453] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5431.193429] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5431.193436] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5431.397387] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5431.397395] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5431.397400] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?

[ 5431.453423] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5431.453513] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5431.657385] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5431.657392] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5431.861386] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5431.861401] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5432.065439] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5432.065458] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5432.269400] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5432.269443] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 5432.269449] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?

[ 5432.269470] hub 1-0:1.0: unable to enumerate USB device on port 1

[ 5679.790900] APIC error on CPU0: 40(40)

[ 5970.966390] ehci_hcd 0000:00:13.2: port 1 reset error -110

[ 5970.966606] hub 1-0:1.0: hub_port_status failed (err = -32)

[ 7332.679969] gvfsd-trash[3420]: segfault at 28 ip 0000000000410114 sp 00007fff0c670040 error 4 in gvfsd-trash[400000+23000]

[ 8520.856764] gvfsd-trash[11076]: segfault at 28 ip 0000000000410114 sp 00007fff14051600 error 4 in gvfsd-trash[400000+23000]

[ 8672.269979] APIC error on CPU0: 40(40)

[ 9368.435662] APIC error on CPU0: 40(40)

[ 9442.033793] APIC error on CPU0: 40(40)

[10181.211745] end_request: I/O error, dev sr0, sector 0

[10181.211759] Buffer I/O error on device sr0, logical block 0

[10181.221696] end_request: I/O error, dev sr0, sector 0

[10181.221709] Buffer I/O error on device sr0, logical block 0

[10181.229696] cdrom: This disc doesn't have any tracks I recognize!

[10207.923790] APIC error on CPU0: 40(40)

[10475.588426] APIC error on CPU0: 40(40)

any help would be awesome. thx

---

### Post by kerry_s on 2009-10-22
usb's do go bad, could this be a hardware issue?

do you have a live cd, before 9.04 that you can try the usb's on?

---

### Post by maxadamo on 2009-10-23
This is not a hardware issue. It seems to be an issue with the latest kernel with MSI Wind Netbooks.
I have same identical problem, other people using this netbook have this problem.

---

### Post by ukripper on 2009-10-23
Can you boot Hardy's or Ibex's Live cd and see if your usbs are detected as expected?

---

### Post by fatzilla on 2009-10-25
so when i use the live cd the usb still wont work so im thinkin im burnt

---

### Post by LewRockwell on 2009-10-25
Do a close physical visual inspection of each and every port with a good strong light and some form of magnification

We have seen abused USB connectors come apart and leave conducting material inside the port thereby creating a shorted condition

.

---

