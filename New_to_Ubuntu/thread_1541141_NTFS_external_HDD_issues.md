---
title: "NTFS external HDD issues"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by viniciuscarvalho on 2010-07-28
Hi there! I have a 2tb external WD 3.5 HD. I was using this device with no problems on my XBMC Live computer (ubuntu 9.04).

Yesterday I accidentally remove it without umounting first. 

My notebook runs an ubuntu 10.04. And when I plugged the drive, it displayed several errors, not being able to mount.

ntfsfix solve the problem.

But now, It simple does not mount on the XBMC PC anymore. It still works on my notebook, but I keep getting errors on the XBMC when it mounts, heres some output of the syslog:

Jul 28 19:18:58 XBMCLive kernel: [ 1113.414966] scsi53 : SCSI emulation for USB Mass Storage devices
Jul 28 19:18:58 XBMCLive kernel: [ 1113.416753] usb-storage: device found at 10
Jul 28 19:18:58 XBMCLive kernel: [ 1113.416760] usb-storage: waiting for device to settle before scanning
Jul 28 19:19:03 XBMCLive kernel: [ 1118.417673] usb-storage: device scan complete
Jul 28 19:19:03 XBMCLive kernel: [ 1118.419370] scsi 53:0:0:0: Direct-Access     WDC WD20 EADS-00S2B0      0A01 PQ: 0 ANSI: 2 CCS
Jul 28 19:19:03 XBMCLive kernel: [ 1118.419700] sd 53:0:0:0: Attached scsi generic sg6 type 0
Jul 28 19:19:03 XBMCLive kernel: [ 1118.422900] sd 53:0:0:0: [sdf] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Jul 28 19:19:03 XBMCLive kernel: [ 1118.424224] sd 53:0:0:0: [sdf] Write Protect is off
Jul 28 19:19:03 XBMCLive kernel: [ 1118.424227] sd 53:0:0:0: [sdf] Mode Sense: 00 38 00 00
Jul 28 19:19:03 XBMCLive kernel: [ 1118.424229] sd 53:0:0:0: [sdf] Assuming drive cache: write through
Jul 28 19:19:03 XBMCLive kernel: [ 1118.428405] sd 53:0:0:0: [sdf] Assuming drive cache: write through
Jul 28 19:19:03 XBMCLive kernel: [ 1118.428464]  sdf: sdf1
Jul 28 19:19:03 XBMCLive kernel: [ 1118.439607] sd 53:0:0:0: [sdf] Assuming drive cache: write through
Jul 28 19:19:03 XBMCLive kernel: [ 1118.439664] sd 53:0:0:0: [sdf] Attached SCSI disk
Jul 28 19:19:07 XBMCLive ntfs-3g[2939]: Version 2009.4.4 external FUSE 27
Jul 28 19:19:07 XBMCLive ntfs-3g[2939]: Mounted /dev/sdf1 (Read-Write, label "", NTFS 3.1)
Jul 28 19:19:07 XBMCLive ntfs-3g[2939]: Cmdline options: rw,nosuid,nodev,sync,uhelper=hal
Jul 28 19:19:07 XBMCLive ntfs-3g[2939]: Mount options: rw,nosuid,nodev,sync,uhelper=hal,silent,allow_other,nonempty,relatime,fsname=/dev/sdf1,blkdev,blksize=4096
Jul 28 19:19:07 XBMCLive hald: mounted /dev/sdf1 on behalf of uid 1000
Jul 28 19:19:53 XBMCLive acpid: client 1507[0:0] has disconnected
Jul 28 19:19:53 XBMCLive acpid: client 1507[0:0] has disconnected
Jul 28 19:19:53 XBMCLive acpid: client connected from 1507[0:0]
Jul 28 19:19:53 XBMCLive acpid: client connected from 1507[0:0]
Jul 28 19:19:56 XBMCLive kernel: [ 1170.967711] usb 1-5: USB disconnect, address 10
Jul 28 19:19:56 XBMCLive kernel: [ 1170.967752] sd 53:0:0:0: [sdf] Unhandled error code
Jul 28 19:19:56 XBMCLive kernel: [ 1170.967754] sd 53:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Jul 28 19:19:56 XBMCLive kernel: [ 1170.967758] end_request: I/O error, dev sdf, sector 488378111
Jul 28 19:19:56 XBMCLive kernel: [ 1170.967762] __ratelimit: 511 callbacks suppressed
Jul 28 19:19:56 XBMCLive kernel: [ 1170.967765] Buffer I/O error on device sdf1, logical block 61047256
Jul 28 19:19:56 XBMCLive kernel: [ 1170.967798] sd 53:0:0:0: [sdf] Unhandled error code
Jul 28 19:19:56 XBMCLive kernel: [ 1170.967800] sd 53:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Jul 28 19:19:56 XBMCLive kernel: [ 1170.967803] end_request: I/O error, dev sdf, sector 488378111
Jul 28 19:19:56 XBMCLive kernel: [ 1170.967805] Buffer I/O error on device sdf1, logical block 61047256
Jul 28 19:19:56 XBMCLive ntfs-3g[2939]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Jul 28 19:19:56 XBMCLive ntfs-3g[2939]: Failed to read index block: Input/output error
Jul 28 19:19:56 XBMCLive hald[849]: forcibly attempting to lazy unmount /dev/sdf1 as enclosing drive was disconnected
Jul 28 19:19:56 XBMCLive ntfs-3g[2939]: Unmounting /dev/sdf1 ()
Jul 28 19:19:56 XBMCLive hald: unmounted /dev/sdf1 from '/media/disk1' on behalf of uid 0
Jul 28 19:19:56 XBMCLive kernel: [ 1171.216235] usb 1-5: new high speed USB device using ehci_hcd and address 11
Jul 28 19:19:56 XBMCLive kernel: [ 1171.420233] usb 1-5: device descriptor read/64, error -71
Jul 28 19:19:57 XBMCLive kernel: [ 1171.728509] usb 1-5: device descriptor read/64, error -71
Jul 28 19:19:57 XBMCLive kernel: [ 1171.944088] usb 1-5: new high speed USB device using ehci_hcd and address 12
Jul 28 19:19:57 XBMCLive kernel: [ 1172.148427] usb 1-5: device descriptor read/64, error -71
Jul 28 19:19:57 XBMCLive kernel: [ 1172.456151] usb 1-5: device descriptor read/64, error -71
Jul 28 19:19:58 XBMCLive kernel: [ 1172.672513] usb 1-5: new high speed USB device using ehci_hcd and address 13
Jul 28 19:19:58 XBMCLive kernel: [ 1173.136326] usb 1-5: device not accepting address 13, error -71
Jul 28 19:19:58 XBMCLive kernel: [ 1173.248208] usb 1-5: new high speed USB device using ehci_hcd and address 14
Jul 28 19:19:59 XBMCLive kernel: [ 1173.712321] usb 1-5: device not accepting address 14, error -71
Jul 28 19:19:59 XBMCLive kernel: [ 1173.712337] hub 1-0:1.0: unable to enumerate USB device on port 5
Jul 28 19:19:59 XBMCLive kernel: [ 1174.152083] usb 3-5: new full speed USB device using ohci_hcd and address 8
Jul 28 19:19:59 XBMCLive kernel: [ 1174.332067] usb 3-5: device descriptor read/64, error -62
Jul 28 19:20:00 XBMCLive kernel: [ 1174.616077] usb 3-5: device descriptor read/64, error -62
Jul 28 19:20:00 XBMCLive kernel: [ 1174.896525] usb 3-5: new full speed USB device using ohci_hcd and address 9
Jul 28 19:20:00 XBMCLive kernel: [ 1175.076228] usb 3-5: device descriptor read/64, error -62
Jul 28 19:20:00 XBMCLive kernel: [ 1175.360506] usb 3-5: device descriptor read/64, error -62
Jul 28 19:20:01 XBMCLive kernel: [ 1175.640149] usb 3-5: new full speed USB device using ohci_hcd and address 10
Jul 28 19:20:01 XBMCLive kernel: [ 1176.048480] usb 3-5: device not accepting address 10, error -62
Jul 28 19:20:01 XBMCLive kernel: [ 1176.224075] usb 3-5: new full speed USB device using ohci_hcd and address 11
Jul 28 19:20:02 XBMCLive kernel: [ 1176.632304] usb 3-5: device not accepting address 11, error -62
Jul 28 19:20:02 XBMCLive kernel: [ 1176.632329] hub 3-0:1.0: unable to enumerate USB device on port 5


Does anyone have any idea on how to get it working again on the 9.04 ubuntu?

Regards

---

