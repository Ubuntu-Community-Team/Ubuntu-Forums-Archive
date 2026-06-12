---
title: "Can't mount camera"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by mutesounds on 2009-05-13
I have a Canon 40D and when I plug it in, it does nothing.  Any other USB device is recognized, but I get nothing with the cam.

---

### Post by Lampi on 2009-05-13
can you show us the output of 'dmesg | tail -n50'? This should show us what udev is trying to do.

---

### Post by mutesounds on 2009-05-13
[  271.918149] usb-storage: device found at 4
[  271.918155] usb-storage: waiting for device to settle before scanning
[  271.918251] scsi7 : SCSI emulation for USB Mass Storage devices      
[  271.918372] usb-storage: device found at 2                           
[  271.918376] usb-storage: waiting for device to settle before scanning
[  271.918484] scsi8 : SCSI emulation for USB Mass Storage devices      
[  271.918593] usb-storage: device found at 11                          
[  271.918597] usb-storage: waiting for device to settle before scanning
[  271.918612] usbcore: registered new interface driver usb-storage     
[  271.918618] USB Mass Storage support registered.                     
[  276.916281] usb-storage: device scan complete                        
[  276.916320] usb-storage: device scan complete                        
[  276.916337] usb-storage: device scan complete                        
[  276.916866] scsi 6:0:0:0: Direct-Access     HP       Photosmart C4280 1.00 PQ: 0 ANSI: 5
[  276.916972] scsi 8:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[  276.925170] scsi 7:0:0:0: Direct-Access     IOI-CFC                        PQ: 0 ANSI: 0 CCS
[  276.934632] scsi 7:0:0:1: Direct-Access     IOI-SMC                        PQ: 0 ANSI: 0 CCS
[  276.940986] scsi 7:0:0:2: Direct-Access     IOI-MMC                        PQ: 0 ANSI: 0 CCS
[  276.947481] scsi 7:0:0:3: Direct-Access     IOI-MSC                        PQ: 0 ANSI: 0 CCS
[  278.716723] sd 8:0:0:0: [sdb] 8060928 512-byte hardware sectors: (4.12 GB/3.84 GiB)
[  278.717296] sd 8:0:0:0: [sdb] Write Protect is off
[  278.717301] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  278.717307] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  278.718840] sd 8:0:0:0: [sdb] 8060928 512-byte hardware sectors: (4.12 GB/3.84 GiB)
[  278.719343] sd 8:0:0:0: [sdb] Write Protect is off
[  278.719348] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  278.719352] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  278.719358]  sdb: sdb1 sdb2 < sdb5 >
[  278.893452] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[  278.893552] sd 8:0:0:0: Attached scsi generic sg2 type 0
[  278.894717] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[  278.894805] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  278.895819] sd 7:0:0:1: [sdd] Attached SCSI removable disk
[  278.895890] sd 7:0:0:1: Attached scsi generic sg4 type 0
[  278.897372] sd 7:0:0:2: [sde] Attached SCSI removable disk
[  278.897452] sd 7:0:0:2: Attached scsi generic sg5 type 0
[  278.898881] sd 7:0:0:3: [sdf] Attached SCSI removable disk
[  278.898961] sd 7:0:0:3: Attached scsi generic sg6 type 0
[  278.900294] sd 6:0:0:0: [sdg] Attached SCSI removable disk
[  278.900387] sd 6:0:0:0: Attached scsi generic sg7 type 0
[  289.330955] usb 1-2: USB disconnect, address 10
[  684.656426] usb 1-1: USB disconnect, address 11
[  691.984025] usb 1-1: new high speed USB device using ehci_hcd and address 12
[  692.118705] usb 1-1: configuration #1 chosen from 1 choice
[  751.295081] usb 1-1: USB disconnect, address 12
[  980.779321] flashplayer-ins[4343]: segfault at bf34cffc ip b7f2f135 sp bf34d000 error 6 in libc-2.9.so[b7eb8000+15c000]
[  980.954697] flashplayer-ins[4366]: segfault at bf2a3ffc ip b7f85156 sp bf2a4000 error 6 in libc-2.9.so[b7f0e000+15c000]
[  980.978348] flashplayer-ins[4320]: segfault at bf104ffc ip b7ee714d sp bf105000 error 6 in libc-2.9.so[b7e70000+15c000]
[  981.099463] flashplayer-ins[4297]: segfault at bf1adffc ip b7e8f135 sp bf1ae000 error 6 in libc-2.9.so[b7e18000+15c000]
[  981.150217] flashplayer-ins[4389]: segfault at bf120f7c ip 0804e00c sp bf120f70 error 6 in dash[8048000+15000]

---

