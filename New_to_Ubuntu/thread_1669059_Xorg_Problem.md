---
title: "Xorg Problem"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by Peter09 on 2011-01-17
Running Maverick on a HP Pavilion with a ATI Mobility Radeon HD 4500 Series.

Been using this O/S since release on this machine, with no real problems. Suddenly I am getting a busy cursor instead of the idle cursor and  an additional 10-15% system load every 20-30 seconds or so, then it will switch back to normal after 5 secs. I think its associated with Xorg, but really cannot see a real culprit.

Anyone else getting this?

Update
Getting this in the log file

> Jan 17 11:52:18 Pavilion kernel: [ 3581.144254] nautilus[6846]: segfault at 0 ip 00007ff1670adec0 sp 00007fffa126c998 error 4 in libglib-2.0.so.0.2600.0[7ff16704b000+e0000]
Jan 17 11:52:43 Pavilion kernel: [ 3606.396024] nautilus[6899]: segfault at 0 ip 00007ffb88c00ec0 sp 00007fff03e81e68 error 4 in libglib-2.0.so.0.2600.0[7ffb88b9e000+e0000]
Jan 17 11:53:08 Pavilion kernel: [ 3631.640759] nautilus[6929]: segfault at 0 ip 00007feefcefcec0 sp 00007fffc53ceba8 error 4 in libglib-2.0.so.0.2600.0[7feefce9a000+e0000]


---

### Post by Peter09 on 2011-01-17
After deleting .gconf and .nautilus I am now getting

> Initializing nautilus-gdu extension

(nautilus:18318): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `SyncdaemonFolderInfo'

** (nautilus:18318): CRITICAL **: syncdaemon_folder_info_get_path: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (nautilus:18318): CRITICAL **: syncdaemon_folder_info_get_volume_id: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (nautilus:18318): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

AnyOne?

---

### Post by Peter09 on 2011-01-17
well it appears to have been a problem with UbuntuOne. removing that resolved it. What exactly was the problem I don't know

---

### Post by Peter09 on 2011-01-17
well it appears to have been a problem with UbuntuOne. removing that resolved it. What exactly was the problem I don't know

---

### Post by fatality_uk on 2011-01-17
Did you do a **dmesg | tail** just after the CPU spiked?

---

