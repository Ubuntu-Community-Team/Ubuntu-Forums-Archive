---
title: "Help! RT5390r wireless driver installation"
date: 2013-09-10
forum: Networking &amp; Wireless
---

### Post by fugue2 on 2013-09-10
I am a newbie in Linux. I installed Ubuntu 13.04 64bit on my HP laptop with a rt5390r wireless adapter but the current driver version is rt2800pci and the wireless connection is very weak and unstable. I searched the forum and found many similar problems, but most of the threads were posted around 2010/2011 and I am not sure whether they still works now. The solutions from those threads are all very similar but after it seems they did not work on mine. This is a typical one that I followed:

[http://ubuntuforums.org/showthread.php?t=1645716](http://ubuntuforums.org/showthread.php?t=1645716)

Can someone please tell me what should I do? Thanks in advance!

---

### Post by varunendra on 2013-09-11
> **fugue2 said:**
> I searched the forum and found many similar problems, but most of the threads were posted around 2010/2011 and I am not sure whether they still works now.

Even the [official driver]("http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501") (RT539x PCIe) listed at Ralink's site is from 2011, and will almost certainly fail to build on 13.04. We may be able to apply some patches to make it successfully compile and install, but I think we should try a few things with the native one first.

Accordingly, please try (if you haven't already) -
```
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```

Do not reboot after this. This is a temporary change that will be lost at next boot. If it helps improving the connection, we can make it permanent.

If it doesn't help, before proposing the proprietary driver (if, first I could build it on 13.04), I would like to see a detailed diagnostics report created by "wireless_script" which you can find in the "Wireless Script" link in my signature. Follow the instructions in the linked post and post back the report here.

---

