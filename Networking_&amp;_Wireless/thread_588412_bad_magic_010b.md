---
title: "bad magic: 010b"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by HondaRacer on 2007-10-23
hi,
i'm having some troble setting up wireless

i; using Z-Com Medion 40900 802.11b Adapter
and WindowsXP driver wlanuig (inf/sys)
on AMD Semprom 3100+ 
ubuntu 7,10 gutsy


output of: dmesg

...
[   26.026689] ndiswrapper version 1.48 loaded (smp=yes, preempt=rt)
[   26.172635] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[   26.321660] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   26.321667] ndiswrapper (load_sys_files:216): couldn't prepare driver 'wlanuig'
[   26.334406] ndiswrapper (load_wrap_driver:118): couldn't load driver wlanuig; check system log for messages from 'loadndisdriver'
[   26.334440] usbcore: registered new interface driver ndiswrapper
...

Anybody help !!!

---

### Post by noob12 on 2007-10-24
It means that you are running the 64-bit version of Ubuntu but that the Windows driver you are trying to use with ndiswrapper is a 32-bit version.

If you can get a 64-bit version of the driver, that might work.  Otherwise, you may want to use the 32-bit version of Ubuntu in order to run this.

---

