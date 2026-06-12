---
title: "Broadcom 4312 wireless (driver?) problems"
date: 2014-10-28
forum: Networking &amp; Wireless
---

### Post by SepLite on 2014-10-28
Using a 32-bit Ubuntu Live USB with persistent storage. When I first select the driver under software/updates, it works even though it says its "not working." However, after restarting, the driver is still selected but no wireless networks appear. From some internet searching, Ubuntu should be compatible with Broadcom 4312.

Not sure what other info I need to post...

---

### Post by chili555 on 2014-10-29
I suspect you have the wrong driver enabled. Please check here: [http://ubuntuforums.org/showthread.php?t=2250096](http://ubuntuforums.org/showthread.php?t=2250096)

---

### Post by SepLite on 2014-10-29
Thanks for the reply!

However, after running sudo apt-get install firmware-b43-installer, it says "Unable to locate package firmware-b43-installer. I'm not sure if this is relevant but b43 is listed when I run lsmod, will this be enough? 

If I run "sudo apt-get purge bcmwl-kernel-source" it returns "Sub-process /usr/bin/dpkg returned an error code (1)" although that doesn't seem very helpful.

**EDIT:** I noticed three errors on boot that were related to the b43 driver, and following the link tells me to do exactly what you said to do(and with the same error of course).
```

b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version.

```

---

### Post by SepLite on 2014-10-29
Here is the full terminal output when running sudo "apt-get purge bcmwl-kernel-source"
```

ubuntu@ubuntu:~$ sudo apt-get purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  bcmwl-kernel-source
0 upgraded, 0 newly installed, 1 to remove and 229 not upgraded.
6 not fully installed or removed.
After this operation, 4,944 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 207663 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
update-initramfs: deferring update (trigger activated)
lzma: (stdin): Cannot allocate memory
dpkg: error processing package bcmwl-kernel-source (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by chili555 on 2014-10-29
First, open Software and Updates. Be sure that main, universe, restricted and multiverse are all selected. Then try again:```
sudo apt-get update
sudo apt-get install  firmware-b43-installer
```After it installs, reboot.

---

