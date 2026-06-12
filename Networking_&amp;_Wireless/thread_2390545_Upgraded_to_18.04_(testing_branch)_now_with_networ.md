---
title: "Upgraded to 18.04 (testing branch) now with networking issues"
date: 2018-04-30
forum: Networking &amp; Wireless
---

### Post by jonnykickinbut on 2018-04-30
I am experiencing some issues with regards to network connections with Network Manager, and also with the applet which has disappeared from the Notification Area completely.   This is following my update to 18.04 last night, with Mate desktop running.  

Currently i cannot access the applet (nm) that is the main way i can graphically connect usually to wifi spots.

Also I am getting some errors in my logs that seem to connect back to this problem, but I am not sure (see below.)

If anyone uses Mate and Ubuntu v18.04 and can verify the working network-manager applet within the Notification Area for mate-panel I would really appreciate it.

Here is the dmesg output from the most recent boot up:

[    5.625019] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[    5.714977] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[   13.124021] Bluetooth: RFCOMM TTY layer initialized
[   13.124028] Bluetooth: RFCOMM socket layer initialized
[   13.124035] Bluetooth: RFCOMM ver 1.11
[   15.028506] FAT-fs (mmcblk0p1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[   17.968352] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[   35.269600] PKCS#7 signature not signed with a trusted key
[   35.280308] vboxdrv: Found 4 processor cores
[   35.300509] vboxdrv: TSC mode is Invariant, tentative frequency 2095122907 Hz
[   35.300511] vboxdrv: Successfully loaded version 5.2.10_Ubuntu (interface 0x00290001)
[   35.309329] PKCS#7 signature not signed with a trusted key
[   35.309793] VBoxNetFlt: Successfully started.
[   35.316754] PKCS#7 signature not signed with a trusted key
[   35.317141] VBoxNetAdp: Successfully started.
[   35.324569] PKCS#7 signature not signed with a trusted key
[   35.325008] VBoxPciLinuxInit
[   35.328324] vboxpci: IOMMU not found (not registered)


Not sure why I am getting this message, following the update to 18.04, but my kernel log has output: 

"PKCS#7 signature not signed with a trusted key" (which it is in red lettering)

---

### Post by jonnykickinbut on 2018-04-30
I found the bug associated with the Networkmanager applet, now I am wondering what else could be wrong, so here is the full dmesg output:

[http://paste.ubuntu.com/p/HHdS8BZXGs/](http://paste.ubuntu.com/p/HHdS8BZXGs/)

Thanks to anyone who has the time and wants to help.

---

