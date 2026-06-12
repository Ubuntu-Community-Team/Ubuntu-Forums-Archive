---
title: "SDHC not being mounted"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by schenier on 2009-01-11
Hello,

I just got a new 8GB micro SDHC card and it can't be found in Ubuntu 8.10.

I have a small card reader that can read SDHC card, so it shouldn't be the problem.

When I put it in the USB slot, I have 'USB Drive' that appears in the file browser. But it is not mounted, and the only option I have (when right clicking it) is to rescan it (besides trying to open it).

I read somewhere else to type 'dmesg | tail' and this is the output :


```
[ 2233.510068] sd 11:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 2233.510076] end_request: I/O error, dev sdb, sector 0
[ 2234.518555] sd 11:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2234.518568] sd 11:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 2234.518577] sd 11:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 2234.518585] end_request: I/O error, dev sdb, sector 0
[ 2234.520556] sd 11:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2234.520564] sd 11:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 2234.520571] sd 11:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 2234.520580] end_request: I/O error, dev sdb, sector 0

```


can someone help me please?

---

### Post by ternanta on 2009-01-20
I'm getting the same behavior for my 4GB and 8GB SDHC card in a small usb adaptor I have. My upto 2 GB SD cards mount fine. But the same otherwise,


Jan 19 14:50:57 unbun2desktop kernel: [ 6434.774412] usb-storage: device found at 2
Jan 19 14:50:57 unbun2desktop kernel: [ 6434.774415] usb-storage: waiting for device to settle before scanning
Jan 19 14:51:02 unbun2desktop kernel: [ 6439.776200] usb-storage: device scan complete
Jan 19 14:51:32 unbun2desktop kernel: [ 6470.021271] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
Jan 19 14:51:33 unbun2desktop kernel: [ 6470.271257] usb-storage: device found at 3
Jan 19 14:51:33 unbun2desktop kernel: [ 6470.271261] usb-storage: waiting for device to settle before scanning
Jan 19 14:51:38 unbun2desktop kernel: [ 6475.268628] usb-storage: device scan complete
Jan 19 14:52:18 unbun2desktop kernel: [ 6515.765658] sd 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
Jan 19 14:52:18 unbun2desktop kernel: [ 6516.036861] usb-storage: device found at 4
Jan 19 14:52:18 unbun2desktop kernel: [ 6516.036866] usb-storage: waiting for device to settle before scanning
Jan 19 14:52:23 unbun2desktop kernel: [ 6521.036650] usb-storage: device scan complete
Jan 19 14:53:31 unbun2desktop kernel: [ 6588.265150] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
Jan 19 14:53:31 unbun2desktop kernel: [ 6588.544125] usb-storage: device found at 5
Jan 19 14:53:31 unbun2desktop kernel: [ 6588.544130] usb-storage: waiting for device to settle before scanning
Jan 19 14:58:18 unbun2desktop kernel: [ 6875.699760] usb-storage: device found at 6
Jan 19 14:58:18 unbun2desktop kernel: [ 6875.699763] usb-storage: waiting for device to settle before scanning
Jan 19 14:58:23 unbun2desktop kernel: [ 6880.696216] usb-storage: device scan complete
Jan 19 14:59:20 unbun2desktop kernel: [ 6937.429577] sd 10:0:0:0: [sdb] Mode Sense: 00 00 00 00
Jan 19 14:59:20 unbun2desktop kernel: [ 6937.682375] usb-storage: device found at 7
Jan 19 14:59:20 unbun2desktop kernel: [ 6937.682381] usb-storage: waiting for device to settle before scanning
Jan 19 14:59:25 unbun2desktop kernel: [ 6942.680711] usb-storage: device scan complete
Jan 19 15:00:06 unbun2desktop kernel: [ 6983.169659] sd 11:0:0:0: [sdb] Mode Sense: 00 00 00 00
Jan 19 15:00:06 unbun2desktop kernel: [ 6983.419633] usb-storage: device found at 8
Jan 19 15:00:06 unbun2desktop kernel: [ 6983.419637] usb-storage: waiting for device to settle before scanning
Jan 19 15:00:11 unbun2desktop kernel: [ 6988.416169] usb-storage: device scan complete

---

