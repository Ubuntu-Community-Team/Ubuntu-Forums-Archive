---
title: "setting up IDEA Netsetter in Ubuntu 10.10"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by anantinvent on 2011-06-30
when i connect my USB device it gives me a message "failed to mount HUAWEI MMC storage" .What should i do?

---

### Post by cariboo on 2011-06-30
What is the output of:

```
dmesg | tail -n10
```

just after you've plugged the device in?

---

### Post by anantinvent on 2011-07-01
thanks for replying..
the output for dmesg | tail -n10 after plugging in the device::
```

[ 1362.418134] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB3
[ 1362.418355] usbcore: registered new interface driver option
[ 1362.418361] option: v0.7.2:USB Driver for GSM modems
[ 1363.341281] scsi 13:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[ 1363.342212] scsi 12:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 1363.342301] sd 13:0:0:0: Attached scsi generic sg2 type 0
[ 1363.353535] sd 13:0:0:0: [sdb] Attached SCSI removable disk
[ 1363.365788] sr1: scsi-1 drive
[ 1363.368724] sr 12:0:0:0: Attached scsi CD-ROM sr1
[ 1363.368910] sr 12:0:0:0: Attached scsi generic sg3 type 5

```

---

### Post by anantinvent on 2011-07-03
someone pls help...

---

