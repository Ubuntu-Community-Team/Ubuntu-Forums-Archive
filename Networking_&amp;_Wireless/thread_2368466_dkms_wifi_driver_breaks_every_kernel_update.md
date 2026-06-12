---
title: "dkms wifi driver breaks every kernel update"
date: 2017-08-11
forum: Networking &amp; Wireless
---

### Post by fates on 2017-08-11
I'm using DKMS to support my usb 3.0 realtek 8812AU wifi. From what I understand this should recompile the module to support my wifi every kernel update. What I am running into is that every time the kernel updates I have to totally remove and reinstall dkms and the 8812au packages. Am I doing this wrong for keeping my system functional as I am looking at upgrading my system to mico ITX box that won't have a supported wifi device to fallback and do this to keep my system on the net.

---

### Post by jeremy31 on 2017-08-11
If you are using the 8812au-dkms package from the repos see [https://askubuntu.com/a/832741/300665](https://askubuntu.com/a/832741/300665) to fix the cause of the problem

---

