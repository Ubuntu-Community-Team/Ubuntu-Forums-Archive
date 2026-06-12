---
title: "Fsck after hibernation. And modem troubles."
date: 2010-12-18
forum: New to Ubuntu
---

### Post by tkzv on 2010-12-18
I am using an Asus EEE PC 4G notebook. With Lucid I had no problems putting it to sleep and waking. After the upgrade to Maverick troubles started.<br />
<br />
Most often it happens like this. I press the computer power switch or click the panel applet and select hibernation in the dialog that appears. It seems to save the freeze information and power down correctly. When I switch it on, fsck starts, then the computer reboots, then it restarts as after being powered down. The freeze information is lost.<br />
<br />
Interestingly, 3G modem (Huawei E1550, locked to a local provider) stops working after that and starts only after a reboot. Lsusb detects the modem as "12d1:1001 Huawei Technologies Co., Ltd. E620", the modem indicates detecting HSDPA network, but no /dev/ttyUSB* files are created.<br />
<br />
I tried searching in /var/log/, but didn't find anything interesting.<br />
<br />
 What should I do to make hibernation work correctly?<br />
<br />
 If there was any damage to the files on disk, how to check the checksums of installed binaries? debsums?

---

