---
title: "No Wi-Fi Adapter Found... Again"
date: 2018-03-15
forum: Networking &amp; Wireless
---

### Post by connerdavis on 2018-03-15
This is the second time since January that my laptop has just decided to break its own Wifi adapter drivers. Last time I was able to fix it by purging and reinstalling bcmwl-kernel-source, but that doesn't seem to be working this time. I've already checked and made sure my computer isn't in secure boot. Here's the link to the results of the wireless script: [http://paste.ubuntu.com/p/GZMsy5xhbG/](http://paste.ubuntu.com/p/GZMsy5xhbG/)


[SIZE=4]Edit: I was able to fix it
[SIZE=2]I had to reinstall linux-headers-generic and once I did that I was able to reinstall bcmwl-kernel-source without issue; and my laptop's wifi is working again. [/SIZE][/SIZE]

---

### Post by Autodave on 2018-03-15
This may or may not help, but it is the very first thing that I do when I get a weird thing happening on a laptop:

1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

### Post by connerdavis on 2018-03-15
No luck, it still says that there's no wifi adapter found after leaving the battery out and the laptop unplugged for ~15 minutes.

---

### Post by praseodym on 2018-03-16
Driver is not signed, so, deactivate SecureBoot in your UEFI

---

