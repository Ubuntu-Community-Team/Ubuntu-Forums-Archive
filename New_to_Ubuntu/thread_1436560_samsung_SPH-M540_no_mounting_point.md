---
title: "samsung SPH-M540 no mounting point"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by joeoshawa on 2010-03-22
I have been trying to mount this phone for a while i managed to get it to see the phone from what i can tell using google. BTW mannaged to muddle my way through using google so far. For some reason i cannot get it to mount. My best guess is that i am not using the correct mounting point. I am using ubuntu 9.10 64 bit.

hwinfo 
disk:
  /dev/sda             Hitachi HDT72101
                       Qualcomm USB MMC Storage
dmesg output
[    6.752106] usb-storage: device scan complete
[    6.759050] scsi 4:0:0:0: Direct-Access     Samsung  Mass Storage     2.31 PQ: 0 ANSI: 2
[    6.759445] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    6.770035] sd 4:0:0:0: [sdb] 3964928 512-byte logical blocks: (2.03 GB/1.89 GiB)
[    6.783040] sd 4:0:0:0: [sdb] Write Protect is off
[    6.783043] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[    6.783046] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    6.815031] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    6.815036]  sdb: sdb1
[    6.853040] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    6.853044] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   12.919708] udev: starting version 147
[   12.932495] lp: driver loaded but no devices found

if someone could help me here it would be greatly appreciated so far this is the only thing keeping windows on my pc grrr i hate windows

---

### Post by joeoshawa on 2010-05-02
looks like nobody pays any attention to my postings when i need help but it seems if you upgrade to the new ubuntu 10.4 this phone works great plug and play. Havent used the modem but way too expensive. To the developers THANKS THANKS THANKS winblows will soon be history.

---

### Post by bornagainlinux on 2010-05-16
Well it seems that something is broken in 10.04 because I cannot get my phone to mount. It says that it is connected, but nothing shows up. I did this before in 9.10 and I know it worked before. So if it works on yours could you let me know what you did?

Thanks.

---

### Post by sandyd on 2010-05-16
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363329](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363329)

---

