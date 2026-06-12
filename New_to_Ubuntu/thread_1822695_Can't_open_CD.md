---
title: "Can't open CD"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by VoXoM on 2011-08-10
It's a picture CD of my wedding.

Error says ```
Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

dmesg | tail says
```
[263849.225054] sr 3:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[263849.225060] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 16 9d d9 00 00 01 00
[263849.225071] end_request: I/O error, dev sr0, sector 5928804
[263849.226863] sr 3:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[263849.226869] sr 3:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[263849.226874] sr 3:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[263849.226880] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 16 9c a1 00 00 01 00
[263849.226892] end_request: I/O error, dev sr0, sector 5927556
[263849.226907] UDF-fs: No anchor found
[263849.226913] UDF-fs: No partition found (1)

```

please help, ty

---

### Post by VoXoM on 2011-08-10
Solved. Installed "goobox"

---

