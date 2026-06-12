---
title: "External Multicard woes."
date: 2009-07-03
forum: New to Ubuntu
---

### Post by Mortrin on 2009-07-03
I am trying to mount a .img file on an SDHC using an external multicard reader. I know an SD card would be at ```
/dev/sde
```, but when I try to mount it there, it claims there is no space available. If I wanted to mount it to this external SD card, what extension should I use?

---

### Post by t0p on 2009-07-03
By "extension", I suspect you mean what the device file name is, ie /dev/sd*.

Open a terminal and input the following command:

```
tail -f /var/log/messages
```

Now, keep the terminal window open, and insert the card.  New lines should be printed to /var/log/messages, telling you its sd* name.  Look at my example:

```
t0p@ubunty:/var/mail$ tail -f /var/log/messages
Jul  3 13:58:55 ubunty pppd[28310]: Connect: ppp0 <--> /dev/ttyACM0
Jul  3 13:58:55 ubunty pppd[28310]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Jul  3 13:58:55 ubunty pppd[28310]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Jul  3 13:58:55 ubunty pppd[28310]: Remote message: Congratulations!
Jul  3 13:58:55 ubunty pppd[28310]: PAP authentication succeeded
Jul  3 13:58:59 ubunty pppd[28310]: Could not determine remote IP address: defaulting to 10.64.64.64
Jul  3 13:58:59 ubunty pppd[28310]: local  IP address 10.158.147.230
Jul  3 13:58:59 ubunty pppd[28310]: remote IP address 10.64.64.64
Jul  3 13:58:59 ubunty pppd[28310]: primary   DNS address 149.254.192.126
Jul  3 13:58:59 ubunty pppd[28310]: secondary DNS address 149.254.201.126
Jul  3 14:06:32 ubunty kernel: [24437.568882] usb 4-3: new high speed USB device using ehci_hcd and address 5
Jul  3 14:06:32 ubunty kernel: [24437.949066] usb 4-3: configuration #1 chosen from 1 choice
Jul  3 14:06:33 ubunty kernel: [24438.897463] usbcore: registered new interface driver libusual
Jul  3 14:06:33 ubunty kernel: [24438.998788] Initializing USB Mass Storage driver...
Jul  3 14:06:33 ubunty kernel: [24439.002074] scsi2 : SCSI emulation for USB Mass Storage devices
Jul  3 14:06:33 ubunty kernel: [24439.005115] usbcore: registered new interface driver usb-storage
Jul  3 14:06:33 ubunty kernel: [24439.005127] USB Mass Storage support registered.
Jul  3 14:06:38 ubunty kernel: [24444.001823] scsi 2:0:0:0: Direct-Access     USB 2.0  Flash Disk       1100 PQ: 0 ANSI: 0 CCS
Jul  3 14:06:38 ubunty kernel: [24444.017266] sd 2:0:0:0: [sdb] 3915776 512-byte hardware sectors (2005 MB)
Jul  3 14:06:38 ubunty kernel: [24444.018280] sd 2:0:0:0: [sdb] Write Protect is off
Jul  3 14:06:38 ubunty kernel: [24444.021262] sd 2:0:0:0: [sdb] 3915776 512-byte hardware sectors (2005 MB)
Jul  3 14:06:38 ubunty kernel: [24444.022398] sd 2:0:0:0: [sdb] Write Protect is off
Jul  3 14:06:38 ubunty kernel: [24444.022423]  sdb: sdb1
Jul  3 14:06:38 ubunty kernel: [24444.023534] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Jul  3 14:06:38 ubunty kernel: [24444.023603] sd 2:0:0:0: Attached scsi generic sg2 type 0

```

As you can see, ubuntu detects the new usb device and calls it sdb.

---

### Post by Mortrin on 2009-07-04
Thank you for that, worked like a charm and have booted ubuntu to my Beagle Board.

---

