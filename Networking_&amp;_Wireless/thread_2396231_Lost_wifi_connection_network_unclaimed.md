---
title: "Lost wifi connection: network unclaimed"
date: 2018-07-12
forum: Networking &amp; Wireless
---

### Post by jonathan81998 on 2018-07-12
Hello all,

I have a dell xps 13 with ubuntu 16.04. I never had any issue with the wifi, but all of a sudden it does not want to connect anymore. There does not seem to be wifi. When I do `sudo lshw -C network`, I have `network UNCLAIMED` (I put the result of `sudo lshw -C network` at the end of the pastebin). I checked on the forums and saw that I might just need to `apt update`, `apt upgrade`, but I don't have internet access on that computer anymore (when I connect ethernet via a usb-c adapter, it does not seem to find ethernet either). Or maybe the problem is elsewhere.

This is the result of the wireless-info script: [https://pastebin.ubuntu.com/p/2BWvj9y6CQ/](https://pastebin.ubuntu.com/p/2BWvj9y6CQ/)

Thank you very much for your help!!

Jonathan

---

### Post by praseodym on 2018-07-13
Please run
```

sudo modprobe -v ath9k
dmesg | egrep 'ath|key|error'
```

---

### Post by jonathan81998 on 2018-07-13
Thank you. I marked the thread as solved as I decided to upgrade to 18.04 to solve it. I did not reply until I was sure it was working. After upgrading to 18.04 with a bootable usb key, my wifi is now workin fine.
Thank you again.

---

### Post by jeremy31 on 2018-07-13
I think you may have had a broken kernel update in 16.04 and it somehow failed to install linux-modules-extra-4.15.0-24-generic as that package contains most of the drivers

---

### Post by jonathan81998 on 2018-07-13
I think I might also have done a `sudo apt autoremove` before the problem, as it was suggested by apt after doing an upgrade. Is that possible that caused the problem? Is it safe to do `sudo apt autoremove`?

---

### Post by jeremy31 on 2018-07-13
I don't think sudo apt autoremove is unsafe and I don't think it caused the issue.  I have seen a few issues with broken kernel installs and linux-modules-extra, in the past it would happen with linux-image-extra occasionally

---

