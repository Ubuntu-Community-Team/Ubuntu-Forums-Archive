---
title: "Dell XPS 13 (BCM4352) Crash when connecting wifi."
date: 2015-04-16
forum: Networking &amp; Wireless
---

### Post by dznn on 2015-04-16
Hi,

I get a kernel panic when I connect to my wifi network. I was hoping someone here could help me solve it.

[LIST]
[*]I have the new Dell XPS 13 (2015), latest bios A03, with a Broadcom BCM4352 wifi adapter.
[*]Installed the daily of the Ubuntu Server image because I wanted a minimal install and I couldn't find minimal or netinstall iso's of the daily.
[*]Installed the bcmwl-kernel-source package which should support my chip from what I could find online.
[*]Used connman to connect.
[/LIST]

The strange thing is, unless I was dreaming I think it did work right after the install, the first run before a reboot.

Kernel:
Linux odin 3.19.0-14-generic #14-Ubuntu SMP Mon Apr 13 22:18:24 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

I logged the panic;
(dmesg log) [http://paste.ubuntu.com/10831802/](http://paste.ubuntu.com/10831802/)
(dump.crash) [http://paste.ubuntu.com/10831804/](http://paste.ubuntu.com/10831804/)
(dump) I have this too but it's 44mb, if required I'll upload it.

Thanks


--Edit--

If people suggest using the dkms package directly, it's broken;
[https://bugs.launchpad.net/ubuntu/+source/broadcom-sta/+bug/1439616](https://bugs.launchpad.net/ubuntu/+source/broadcom-sta/+bug/1439616)

Also this might be the bug I experience, but it happens every time for me:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1421833](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1421833)

The Arch wiki they link to says it's solved for the BCM4352 but I can't use the b43 driver because it doesn't support my chip yet;
[http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/](http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/)

--Edit 2--

This seemed to have been a connman issue. When using Wicd it doesn't happen.

---

### Post by dino99 on 2015-04-16
related bcm4352 thread [http://ubuntuforums.org/showthread.php?t=2197997](http://ubuntuforums.org/showthread.php?t=2197997)

something strange:
- '_ART package 0 is invalid, ignored' which seems related to android
- 2 'crashkernel=' set as boot parameters

---

### Post by dznn on 2015-04-16
> **9d9 said:**
> related bcm4352 thread [http://ubuntuforums.org/showthread.php?t=2197997](http://ubuntuforums.org/showthread.php?t=2197997)

This thread is very old and doesn't contain a solution.

> **9d9 said:**
> 
something strange:
- '_ART package 0 is invalid, ignored' which seems related to android
- 2 'crashkernel=' set as boot parameters
The crashkernel parameter is required for me to log the kernel panic. I have no idea where the  ART comes from (I do have the Android SDK installed but that's totaly unrelated).

---

### Post by dino99 on 2015-04-16
your logs does not show other way to dig; maybe add 'debug' to the bootloader to get more details

an other more recent thread  [http://ubuntuforums.org/showthread.php?t=2262459](http://ubuntuforums.org/showthread.php?t=2262459)

---

### Post by cnbiz850 on 2015-06-06
Hi dznn,

I am looking to install Ubuntu on this laptop.  You mentioned about the "daily Ubuntu server image",  I presume it was the daily of 15.04 which is now fully released.  Does the released version run well?

---

