---
title: "unnecessary ATI x-org driver crashed my install"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by Matt__ on 2010-06-06
I have ubuntu 10.04 desktop installed on my dell netbook mini10v.
after some wireless woes its been working great...until the last update when Ubuntu tried to install an ATI based xorg driver which crashed the update and froze ubuntu completely. forced reboot.

on reboot...nothing, no grub, no drop to terminal, no way to access ubuntu at all, just an endless cycle of reboot reboot reboot.

Ok so dell 10v dosnt have ANY ATI hardware in it at all...whats going on lol?

going to reinstall now and see if it tries to mess up xorg again but I would dearly love to know what happened and why its trying to install ati drivers.

---

### Post by sandyd on 2010-06-06
> **Matt__ said:**
> I have ubuntu 10.04 desktop installed on my dell netbook mini10v.
after some wireless woes its been working great...until the last update when Ubuntu tried to install an ATI based xorg driver which crashed the update and froze ubuntu completely. forced reboot.

on reboot...nothing, no grub, no drop to terminal, no way to access ubuntu at all, just an endless cycle of reboot reboot reboot.

Ok so dell 10v dosnt have ANY ATI hardware in it at all...whats going on lol?

going to rreinstall now and see if it tries to mess up xorg again but I would dearly love to know what happened and why its trying to install ati drivers.
theirs an easy fix. boot into recovery mode and
```

sudo apt-get remove fglrx
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by Matt__ on 2010-06-07
Thanks Carlee, but there was no recovery mode, nothing but the boot  screen with option to enter bios or choose boot device..choosing any  boot device caused immediate reboot.

now i cant seem to reinstall any version ..tried 8.04/9.04/10.04 desktop and 9.10 UNR.

errors copying file...the following file did not match its source copy (10.04)
/target/lib/modules/2.6.32-21-generic/
/target/lib/kernel/drivers/scsi/lpfc/lpfc.ko
/target/usr/lib/libnetsnmpmibs.so.15.12
usr/libs/libsmbclient.so.0

install then crashes.

I get similar and varied errors from several disks & versions and same from usb install.
times like these i realise i know jack s*** :P

---

### Post by Matt__ on 2010-06-07
tried a systematic approach.

no combination of discs/usb/vesions/formats worked.
memory tested ok. 
discs tested ok.
USB tested ok.
So I took the netbook apart, checked all conections...still no joy.
SSD worked fine on other machines.
fianlly swapped out the 2Gb of Crucial RAM that had been sat in the machine this last month working perfectly..replaced it with original 1Gb of Samsung RAM.

10.04 installed flawlessly !!!!

the Crucial RAM has since been tested and is 100% ok, so something in that last Lucid update dosnt like my 2Gb stick of ram?
The crucial ram runs fine with 10.04 fully updated on my other laptop however...so Im still mystified as to what happened.

---

### Post by sandyd on 2010-06-07
in the future, try holding down esc or shift to see the grub menu (which will show the recovery options).

I keep on forgetting that other people are not like me... they don't have a dual boot...

---

