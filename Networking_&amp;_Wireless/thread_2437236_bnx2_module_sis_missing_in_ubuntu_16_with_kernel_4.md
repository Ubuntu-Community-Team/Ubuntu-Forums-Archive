---
title: "bnx2 module sis missing in ubuntu 16 with kernel 4.8.0-56"
date: 2020-02-20
forum: Networking &amp; Wireless
---

### Post by sam-alekseev on 2020-02-20
Hi

I upgraded the server dell r510 to ubuntu 16.04 and then installed kernel 4.8.0-56.
after that I lost my motherboard network card Broadcom BCM5716, I found that there is no module bnx2 in the OS.
I did several attempts to compile the driver but no luck.

Could anybody help me with that?

---

### Post by oldfred on 2020-02-20
Thread closed Duplicate
Please do not post duplicate threads on same issue.
We all are volunteers and need to know what already had been suggested to avoid duplication.

See
[https://ubuntuforums.org/showthread.php?t=2437236](https://ubuntuforums.org/showthread.php?t=2437236)

---

### Post by oldfred on 2020-02-20
You may need 16.04.1 as newer kernels obsoleted the SIS driver.

The stock kernel of Ubuntu 17.04 is doing away with Direct Rendering Manager (DRM) support for a number of ancient graphics processors.
3Dfx Banshee/Voodoo3+, ATI Rage 128, Matrox G200/G400, SIS, VIA, and Savage hardware
This was done because they expose insecure APIs to user-space. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276)
[https://www.phoronix.com/scan.php?page=news_item&px=ATI-RAGE-128-DDX-6.11.0](https://www.phoronix.com/scan.php?page=news_item&px=ATI-RAGE-128-DDX-6.11.0)


Do not know if this works or not:
New SIS driver Dec 2019
[https://www.phoronix.com/scan.php?page=news_item&px=xf86-video-sis-0.12.0](https://www.phoronix.com/scan.php?page=news_item&px=xf86-video-sis-0.12.0)

---

