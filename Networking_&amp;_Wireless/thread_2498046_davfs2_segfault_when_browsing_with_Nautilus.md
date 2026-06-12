---
title: "davfs2 segfault when browsing with Nautilus"
date: 2024-05-28
forum: Networking &amp; Wireless
---

### Post by vtpieter on 2024-05-28
After updating to Ubuntu 2024.4 with Gnome 46, Nautilus (files) shows the following error when browsing a davfs share: error opening directory 'transfer endpoint is not connected'

This effectively kills the mount and I find back the following in the logs:
```

kernel: mount.davfs[8855]: segfault at 0 ip 00007814bc044055 sp 00007ffee3439c30 error 4 in libneon.so.27.6.0[7814bc03e000+18000] likely on CPU 4 (core 0, socket 0)
kernel: Code: 56 41 55 41 54 41 89 f4 41 83 e4 01 53 48 89 fb 41 f7 dc 66 41 81 e4 83 73 44 89 e0 48 83 ec 18 80 cc 40 83 e6 02 44 0f 45 e0 <0f> b6 07 84 c0 0f 84 c8 00 00 00 48 89 fa 4>
gnome-shell[3479]: Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2200214
nautilus[47494]: g_object_weak_ref: assertion 'G_IS_OBJECT (object)' failed

```

If I browse from a terminal this does not happen so it seems related to nautilus although the segmentation fault is thrown by davfs.

---

