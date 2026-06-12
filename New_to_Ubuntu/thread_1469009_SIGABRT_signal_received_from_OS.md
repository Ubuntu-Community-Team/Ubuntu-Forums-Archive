---
title: "SIGABRT signal received from OS"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by mistypotato on 2010-05-01
I just installed 9.10 on a Dell Laptop.

It runs REALLY well on it but occasionally I get the following message accompanied by an expected application closure.....

**SIGABRT signal received from OS**

Anyone know if this is an Ubuntu bug in the OS ?

In this case it refers to newt-specific-c->fatal_error#308 and occurred while running Mondorescue right before it started to burn a DVD

But it also happens a LOT when I have MySQL Administrator GUI open.  (no CD involved at all)

---

### Post by madjr on 2010-05-01
why not lucid ?

might work better

---

### Post by ibuclaw on 2010-05-01
> **madjr said:**
> why not lucid ?

might work better

Each to his own. I still run 7.10 on one or two machines...


@OP, can you provide more information?

eg: system logs
```
dmesg
```
or
```
cat /var/log/messages
```

---

### Post by mistypotato on 2010-05-02
May  1 21:18:51 kitten kernel: [15791.553050] usb 2-8: new full speed USB device using ohci_hcd and address 4
May  1 21:18:51 kitten kernel: [15791.762605] usb 2-8: configuration #1 chosen from 1 choice
May  1 21:18:51 kitten kernel: [15791.828421] scsi13 : SCSI emulation for USB Mass Storage devices
May  1 21:18:56 kitten kernel: [15796.844704] scsi 13:0:0:0: Direct-Access     USB-DISK FreeDik-FlashUsb 1.00 PQ: 0 ANSI: 0 CCS
May  1 21:18:56 kitten kernel: [15796.880052] sd 13:0:0:0: [sde] 262112 512-byte hardware sectors (134 MB)
May  1 21:18:56 kitten kernel: [15796.885966] sd 13:0:0:0: [sde] Write Protect is off
May  1 21:18:56 kitten kernel: [15796.911965] sd 13:0:0:0: [sde] 262112 512-byte hardware sectors (134 MB)
May  1 21:18:56 kitten kernel: [15796.918946] sd 13:0:0:0: [sde] Write Protect is off
May  1 21:18:56 kitten kernel: [15796.919748]  sde:
May  1 21:18:56 kitten kernel: [15796.931260] sd 13:0:0:0: [sde] Attached SCSI removable disk
May  1 21:18:56 kitten kernel: [15796.931816] sd 13:0:0:0: Attached scsi generic sg5 type 0
May  1 21:19:48 kitten kernel: [15848.237774] usb 2-8: USB disconnect, address 4
May  1 21:19:48 kitten kernel: [15848.241636] lost page write due to I/O error on sde
May  1 21:19:48 kitten kernel: [15848.241659] lost page write due to I/O error on sde
May  1 21:19:48 kitten kernel: [15848.241674] lost page write due to I/O error on sde
May  1 21:19:48 kitten kernel: [15848.241689] lost page write due to I/O error on sde
May  1 21:19:48 kitten kernel: [15848.241699] lost page write due to I/O error on sde
May  1 21:19:48 kitten kernel: [15848.241714] lost page write due to I/O error on sde
May  1 21:19:48 kitten kernel: [15848.241728] lost page write due to I/O error on sde
May  1 21:19:48 kitten kernel: [15848.241739] lost page write due to I/O error on sde
May  1 21:19:48 kitten kernel: [15848.241754] lost page write due to I/O error on sde
May  1 21:19:48 kitten kernel: [15848.241765] lost page write due to I/O error on sde
May  1 21:20:47 kitten kernel: [15908.020037] usb 2-8: new full speed USB device using ohci_hcd and address 5
May  1 21:20:48 kitten kernel: [15908.232999] usb 2-8: configuration #1 chosen from 1 choice
May  1 21:20:48 kitten kernel: [15908.260041] scsi14 : SCSI emulation for USB Mass Storage devices
May  1 21:20:53 kitten kernel: [15913.298307] scsi 14:0:0:0: Direct-Access     USB-DISK FreeDik-FlashUsb 1.00 PQ: 0 ANSI: 0 CCS
May  1 21:20:53 kitten kernel: [15913.309270] sd 14:0:0:0: [sde] 262112 512-byte hardware sectors (134 MB)
May  1 21:20:53 kitten kernel: [15913.316286] sd 14:0:0:0: [sde] Write Protect is off
May  1 21:20:53 kitten kernel: [15913.358295] sd 14:0:0:0: [sde] 262112 512-byte hardware sectors (134 MB)
May  1 21:20:53 kitten kernel: [15913.365263] sd 14:0:0:0: [sde] Write Protect is off
May  1 21:20:53 kitten kernel: [15913.366057]  sde:
May  1 21:20:53 kitten kernel: [15913.377509] sd 14:0:0:0: [sde] Attached SCSI removable disk
May  1 21:20:53 kitten kernel: [15913.377990] sd 14:0:0:0: Attached scsi generic sg5 type 0
May  1 21:21:22 kitten kernel: [15942.326824] usb 2-8: USB disconnect, address 5
May  1 21:21:22 kitten kernel: [15942.330870] __ratelimit: 3 callbacks suppressed
May  1 21:21:22 kitten kernel: [15942.330896] lost page write due to I/O error on sde
May  1 21:21:22 kitten kernel: [15942.330910] lost page write due to I/O error on sde
May  1 21:21:22 kitten kernel: [15942.330921] lost page write due to I/O error on sde
May  1 21:21:22 kitten kernel: [15942.330930] lost page write due to I/O error on sde
May  1 21:21:22 kitten kernel: [15942.330942] lost page write due to I/O error on sde
May  1 21:21:22 kitten kernel: [15942.330966] lost page write due to I/O error on sde
May  1 21:21:22 kitten kernel: [15942.330976] lost page write due to I/O error on sde
May  1 21:21:22 kitten kernel: [15942.330990] lost page write due to I/O error on sde
May  1 21:21:22 kitten kernel: [15942.331004] lost page write due to I/O error on sde
May  1 21:21:22 kitten kernel: [15942.331020] lost page write due to I/O error on sde
May  1 21:28:06 kitten kernel: [16346.969042] usb 2-8: new full speed USB device using ohci_hcd and address 6
May  1 21:28:07 kitten kernel: [16347.182812] usb 2-8: configuration #1 chosen from 1 choice
May  1 21:28:07 kitten kernel: [16347.200156] scsi15 : SCSI emulation for USB Mass Storage devices
May  1 21:28:12 kitten kernel: [16352.215584] scsi 15:0:0:0: Direct-Access     USB-DISK FreeDik-FlashUsb 1.00 PQ: 0 ANSI: 0 CCS
May  1 21:28:12 kitten kernel: [16352.227553] sd 15:0:0:0: [sde] 262112 512-byte hardware sectors (134 MB)
May  1 21:28:12 kitten kernel: [16352.241239] sd 15:0:0:0: [sde] Write Protect is off
May  1 21:28:12 kitten kernel: [16352.265741] sd 15:0:0:0: [sde] 262112 512-byte hardware sectors (134 MB)
May  1 21:28:12 kitten kernel: [16352.285030] sd 15:0:0:0: [sde] Write Protect is off
May  1 21:28:12 kitten kernel: [16352.285065]  sde:
May  1 21:28:12 kitten kernel: [16352.312058] sd 15:0:0:0: [sde] Attached SCSI removable disk
May  1 21:28:12 kitten kernel: [16352.312304] sd 15:0:0:0: Attached scsi generic sg5 type 0
May  1 21:28:27 kitten kernel: [16368.085742] usb 2-8: USB disconnect, address 6
May  1 21:28:27 kitten kernel: [16368.089525] __ratelimit: 2 callbacks suppressed
May  1 21:28:27 kitten kernel: [16368.089547] lost page write due to I/O error on sde
May  1 21:28:27 kitten kernel: [16368.089559] lost page write due to I/O error on sde
May  1 21:28:27 kitten kernel: [16368.089574] lost page write due to I/O error on sde
May  1 21:28:27 kitten kernel: [16368.089593] lost page write due to I/O error on sde
May  1 21:28:27 kitten kernel: [16368.089608] lost page write due to I/O error on sde
May  1 21:28:27 kitten kernel: [16368.089619] lost page write due to I/O error on sde
May  1 21:28:27 kitten kernel: [16368.089635] lost page write due to I/O error on sde
May  1 21:28:27 kitten kernel: [16368.089645] lost page write due to I/O error on sde
May  1 21:28:27 kitten kernel: [16368.089663] lost page write due to I/O error on sde
May  1 21:28:27 kitten kernel: [16368.089695] lost page write due to I/O error on

---

