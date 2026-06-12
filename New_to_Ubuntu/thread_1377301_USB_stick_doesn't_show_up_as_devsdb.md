---
title: "USB stick doesn't show up as /dev/sdb"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Azrael3000 on 2010-01-10
Hi all,

I have a USB stick that my Ubuntu doesn't like. The log file (/var/log/messages) is as follows:

```

Jan 10 10:35:03 *** kernel: [ 4667.228064] usb 1-2: new high speed USB device using ehci_hcd and address 6
Jan 10 10:35:04 *** kernel: [ 4667.360548] usb 1-2: configuration #1 chosen from 1 choice
Jan 10 10:35:04 *** kernel: [ 4667.363101] scsi5 : SCSI emulation for USB Mass Storage devices
Jan 10 10:35:09 *** kernel: [ 4672.360808] scsi 5:0:0:0: Direct-Access     ChipsBnk Flash Disk       5.00 PQ: 0 ANSI: 2
Jan 10 10:35:09 *** kernel: [ 4672.361756] sd 5:0:0:0: Attached scsi generic sg2 type 0
Jan 10 10:35:09 *** kernel: [ 4672.380506] sd 5:0:0:0: [sdb] 16384 512-byte logical blocks: (8.38 MB/8.00 MiB)
Jan 10 10:35:09 *** kernel: [ 4672.380999] sd 5:0:0:0: [sdb] Write Protect is off
Jan 10 10:35:09 *** kernel: [ 4672.383124]  sdb: unknown partition table
Jan 10 10:35:09 *** kernel: [ 4672.390628] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Jan 10 10:35:39 *** kernel: [ 4703.112066] usb 1-2: reset high speed USB device using ehci_hcd and address 6
Jan 10 10:35:39 *** kernel: [ 4703.244139] usb 1-2: device firmware changed
Jan 10 10:35:39 *** kernel: [ 4703.244187] sd 5:0:0:0: Device offlined - not ready after error recovery
Jan 10 10:35:39 *** kernel: [ 4703.244209] sd 5:0:0:0: [sdb] Unhandled error code
Jan 10 10:35:39 *** kernel: [ 4703.244215] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Jan 10 10:35:39 *** kernel: [ 4703.244355] sd 5:0:0:0: [sdb] Unhandled error code
Jan 10 10:35:39 *** kernel: [ 4703.244360] sd 5:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jan 10 10:35:39 *** kernel: [ 4703.244393] usb 1-2: USB disconnect, address 6
Jan 10 10:35:40 *** kernel: [ 4703.364417] usb 1-2: new high speed USB device using ehci_hcd and address 7
Jan 10 10:35:40 *** kernel: [ 4703.497053] usb 1-2: configuration #1 chosen from 1 choice
Jan 10 10:35:40 *** kernel: [ 4703.499885] scsi6 : SCSI emulation for USB Mass Storage devices
Jan 10 10:35:45 *** kernel: [ 4708.500656] scsi 6:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2
Jan 10 10:35:45 *** kernel: [ 4708.501624] sd 6:0:0:0: Attached scsi generic sg2 type 0
Jan 10 10:35:45 *** kernel: [ 4708.517131] sd 6:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
Jan 10 10:35:45 *** kernel: [ 4708.517875] sd 6:0:0:0: [sdb] Using 0xffffffff as device size
Jan 10 10:35:45 *** kernel: [ 4708.517882] sd 6:0:0:0: [sdb] 4294967296 512-byte logical blocks: (2.19 TB/2.00 TiB)
Jan 10 10:35:45 *** kernel: [ 4708.518375] sd 6:0:0:0: [sdb] Write Protect is off
Jan 10 10:35:45 *** kernel: [ 4708.518998] sd 6:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
Jan 10 10:35:45 *** kernel: [ 4708.519748] sd 6:0:0:0: [sdb] Using 0xffffffff as device size
Jan 10 10:35:45 *** kernel: [ 4708.520788]  sdb:
Jan 10 10:35:45 *** kernel: [ 4708.521622] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.521627] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.521631] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:35:45 *** kernel: [ 4708.521640] __ratelimit: 23 callbacks suppressed
Jan 10 10:35:45 *** kernel: [ 4708.522495] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.522499] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.522502] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:35:45 *** kernel: [ 4708.523377] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.523381] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.523384] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:35:45 *** kernel: [ 4708.526540] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.526545] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.526551] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:35:45 *** kernel: [ 4708.527386] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.527392] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.527397] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:35:45 *** kernel: [ 4708.529662] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.529668] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.529674] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:35:45 *** kernel: [ 4708.530520] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.530526] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.530532] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:35:45 *** kernel: [ 4708.531379] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.531384] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.531389] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:35:45 *** kernel: [ 4708.535636] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.535643] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.535649] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:35:45 *** kernel: [ 4708.535680] Dev sdb: unable to read RDB block 0
Jan 10 10:35:45 *** kernel: [ 4708.536502] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.536508] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.536513] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:35:45 *** kernel: [ 4708.540409] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.540415] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.540421] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:35:45 *** kernel: [ 4708.541375] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.541380] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.541386] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:35:45 *** kernel: [ 4708.542445] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.542451] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.542457] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:35:45 *** kernel: [ 4708.543374] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.543379] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.543384] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:35:45 *** kernel: [ 4708.546440] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.546445] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.546451] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:35:45 *** kernel: [ 4708.546470]  unable to read partition table
Jan 10 10:35:45 *** kernel: [ 4708.551452] sd 6:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
Jan 10 10:35:45 *** kernel: [ 4708.552486] sd 6:0:0:0: [sdb] Using 0xffffffff as device size
Jan 10 10:35:45 *** kernel: [ 4708.554283] sd 6:0:0:0: [sdb] Attached SCSI disk
Jan 10 10:35:45 *** kernel: [ 4708.558628] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:35:45 *** kernel: [ 4708.558635] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:35:45 *** kernel: [ 4708.558641] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:36:15 *** kernel: [ 4739.112057] usb 1-2: reset high speed USB device using ehci_hcd and address 7
Jan 10 10:36:46 *** kernel: [ 4770.112055] usb 1-2: reset high speed USB device using ehci_hcd and address 7
Jan 10 10:37:17 *** kernel: [ 4801.112057] usb 1-2: reset high speed USB device using ehci_hcd and address 7
Jan 10 10:37:48 *** kernel: [ 4832.112107] usb 1-2: reset high speed USB device using ehci_hcd and address 7
Jan 10 10:38:19 *** kernel: [ 4863.112086] usb 1-2: reset high speed USB device using ehci_hcd and address 7
Jan 10 10:38:50 *** kernel: [ 4894.112055] usb 1-2: reset high speed USB device using ehci_hcd and address 7
Jan 10 10:38:50 *** kernel: [ 4894.244805] sd 6:0:0:0: [sdb] Unhandled error code
Jan 10 10:38:50 *** kernel: [ 4894.244813] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Jan 10 10:38:50 *** kernel: [ 4894.244831] __ratelimit: 6 callbacks suppressed
Jan 10 10:38:50 *** kernel: [ 4894.245783] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:38:50 *** kernel: [ 4894.245792] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:38:50 *** kernel: [ 4894.245802] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 10:38:50 *** kernel: [ 4894.246654] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 10:38:50 *** kernel: [ 4894.246663] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 10:38:50 *** kernel: [ 4894.246672] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 11:02:51 *** kernel: [ 6335.120477] usb 1-2: reset high speed USB device using ehci_hcd and address 7
Jan 10 11:03:22 *** kernel: [ 6366.116107] usb 1-2: reset high speed USB device using ehci_hcd and address 7
Jan 10 11:03:53 *** kernel: [ 6397.112087] usb 1-2: reset high speed USB device using ehci_hcd and address 7
Jan 10 11:04:24 *** kernel: [ 6428.116102] usb 1-2: reset high speed USB device using ehci_hcd and address 7
Jan 10 11:04:55 *** kernel: [ 6459.117055] usb 1-2: reset high speed USB device using ehci_hcd and address 7
Jan 10 11:05:26 *** kernel: [ 6490.118109] usb 1-2: reset high speed USB device using ehci_hcd and address 7
Jan 10 11:05:26 *** kernel: [ 6490.252758] sd 6:0:0:0: [sdb] Unhandled error code
Jan 10 11:05:26 *** kernel: [ 6490.252767] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Jan 10 11:05:26 *** kernel: [ 6490.252786] __ratelimit: 22 callbacks suppressed
Jan 10 11:05:26 *** kernel: [ 6490.253993] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 11:05:26 *** kernel: [ 6490.254002] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 11:05:26 *** kernel: [ 6490.254012] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
Jan 10 11:05:26 *** kernel: [ 6490.254858] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 10 11:05:26 *** kernel: [ 6490.254866] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Jan 10 11:05:26 *** kernel: [ 6490.254875] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range

```

Now I don't care about the data on the stick. But the problem is that the device doesn't even show up in /dev so I can't use any program like parted to format the drive. I also tried gpart without luck.
When the stick is attached in Windows XP it does show up but it says it is unformatted. Trying the standard format utility doesn't work either. From what I remember the stick was formated in NTFS.

Anything I could do to repair this thing? Also if there would be an appropriate Windows tool I can give it a try too.

Thanks in advance for your help,
Arno

---

### Post by Redache on 2010-01-10
You could try formatting it to fat32 in Windows, Windows has formatting tools built in (that were originally designed for floppies). 

Once formatted try it in Ubuntu again and see if it auto mounts(Which it should).

Post back with any updates and I'll try and help you further.

---

### Post by scratman on 2010-01-10
Is it possible to install gparted in Windows?  If so, and the Windows formatter cant, you coule probably use gparted in Windows to format to a Linux Friendly format.

---

### Post by Azrael3000 on 2010-01-10
Okay a little update:

I did try to format it on Windows but it didn't work (maybe I was a bit unclear above).

Since I needed to start my LiveCD I found out that I was able to mount the stick there (automount). Started gparted and formatted it to EXT4. Everything seemed to work but when I removed the stick and plugged it back in (still with LiveCD) I get the same error.

---

### Post by Redache on 2010-01-10
It looks like it might be something wrong with the USB stick itself then. Normally Windows would reformat it regardless of what FileSystem was originally on it.

---

### Post by chriswattsgbr on 2011-04-24
This has happened to me and it was because the USB memory stick was counterfeit. I bought it on eBay. There is a lot of cheap junk memory coming out of China lately.

---

