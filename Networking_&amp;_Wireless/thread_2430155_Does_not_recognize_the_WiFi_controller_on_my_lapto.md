---
title: "Does not recognize the WiFi controller on my laptop"
date: 2019-10-28
forum: Networking &amp; Wireless
---

### Post by lordofscripts on 2019-10-28
I am trying out Ubuntu 19 on an Acer Aspire V5-471 laptop but it does not recognize the WiFi controller on it. Under windows it recognizes both the 2,4GHz and 5GHz channels, on Ubuntu it does  not recognize the WiFi hardware. Using the ethernet adapter is cumbersome. What do I need to do to get WiFi working on this. According to the Acer page it is a Broadcom or Atheros, I do not know for sure

[https://www.acer.com/ac/es/ES/content/support-product/4248](https://www.acer.com/ac/es/ES/content/support-product/4248)

---

### Post by wildmanne39 on 2019-10-28
Hello and welcome to the forum, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created and someone should be able to help you.

---

### Post by lordofscripts on 2019-10-28
Checking the script output I found the [0280] line and it says **Broadcom**.

03:00.0 Network controller [0280]: **Broadcom Inc. **and subsidiaries BCM43228 802.11a/b/g/n [**14e4:4359**]
    Subsystem: **Foxconn International, Inc. BCM43228** 802.11a/b/g/n [105b:e04b]
    Kernel driver in use: bcma-pci-bridge

That same line shows [14e4:4359] which I looked up in [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110) and points to :
bcmwl-kernel-source

So I did the *sudo apt-get install bcmwl-kernel-source* and it ran well except it kind of crapped out in the end with the message shown below.
I think I can assume that happened because I have not installed Ubuntu yet, I am running it from a live CD.

Running module version sanity check.
modinfo: ERROR: missing module or filename.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.3.0-18-generic/updates/dkms/

depmod..............

DKMS: install completed.
update-initramfs is disabled since running on read-only media
Processing triggers for man-db (2.8.7-3) ...

or have I made an incorrect assumption?

---

### Post by wildmanne39 on 2019-10-28
Please post all the output from the script in the manner the directions state, so we can better understand what is going on with your wifi.

Thanks

---

