---
title: "ndiswrapper Dell D620 Broadcom 4311 issue"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by chaag on 2006-08-30
Hi,

bcm43xx-fwcutter does not appear to work for me. The kernel never "sees" the drivers and will not load it.

So... I tried ndiswrapper and it appears to work:
chaag@chaag-laptop1:/etc/ndiswrapper$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

depmod -a gives no errors

However, the kernel does not seem to want to load the actual driver, here is dmesg:
[17179592.612000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179592.704000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'strrchr'
[17179592.704000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmFreeContiguousMemorySpecifyCache'
[17179592.704000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmAllocateContiguousMemorySpecifyCache'
[17179592.704000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmGetPhysicalAddress'
[17179592.704000] ndiswrapper (load_sys_files:218): couldn't prepare driver 'bcmwl5'
[17179592.704000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

and from messages
Aug 30 09:55:03 chaag-laptop1 loadndisdriver: loadndisdriver: load_driver(361): couldn't load driver bcmwl5
Aug 30 09:55:03 chaag-laptop1 kernel: [17181269.992000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)


from the begining, lspci shows:
0000:0c:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)


thanks to any and all
just FYI, I managed to get Broadcom 4306 working using bcm43xx-fwcutter on a Dell D600, so I am inclined to use bcm43xx. However, I suspect that, as the kernel never recognizes the chipset, ndis will be the best path here.

---

### Post by haiku99 on 2006-08-30
fwcutter will NOT work w/ the BCM4311, however I did get ndiswrapper to work w/ mine, but had problems until I installed the latest version, 1.23 a/o a couple of weeks ago...there is info on how to get and install the current version at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by chaag on 2006-08-30
works like a charm, thanks!!!

---

