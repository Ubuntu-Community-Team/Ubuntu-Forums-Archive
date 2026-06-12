---
title: "[SOLVED] Disk Usage"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by gettinoriginal on 2008-12-07
I snapped a picture of my System Monitor File Systems, and have no clue what it all means.  Can someone tell me what all these mean ??

[ATTACH]95579[/ATTACH]

---

### Post by dark_harmonics on 2008-12-07
If you go to edit-> preferences-> Filesystems-> uncheck the show all filesystems option it will switch back to a more "normal" view.

---

### Post by snova on 2008-12-07
In order:

[LIST]
[*] The device
[*] The mount point
[*] The filesystem type
[*] The size of the device
[*] The amount of free space on the device
[*] (This one looks exactly the same. No clue.)
[*] The amount of used space on the device
[*] A graphical representation of how much space is used.
[/LIST]

Many of these "devices" do not exist. Some are psuedo-filesystems exported by the kernel for various purposes. I do not understand some of the rest.

The only ones that apply to actual disk partitions are the ones starting with /dev in the device name.

---

