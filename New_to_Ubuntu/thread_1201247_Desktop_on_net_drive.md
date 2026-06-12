---
title: "Desktop on net drive?"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by jbuczek on 2009-06-30
I have two computers:

Mini: a Jetway SBC mini box (1.2 Ghz, 1 GB RAM) running Ubuntu ibex.
Max:  a standard ATX box (P4, 2.8GHz, 1 GB RAM) dual booting ubuntu/Win

Mini acts as a printer server, file server and backup server for my household network of 4 computers. It's left on 24/7.  Even so 90% of the time it's idle.  

Just so I don't have to use the big, watt chomping box for quick easy things, I've tended to just use Mini for email, web surfing, record keeping (in TreePad) and quick and dirty documents.  I've put all my documents on a net drive (//Mini/Archive) so they're accessable from either computer.  The drive (//Mini/Archive) is FAT32 on a USB port so if the server is down and I absolutely must get at my doc's, I can unplug it and mount it on any computer, Linux or Win.

Unfortunately I find myself constantly jumping back and forth to pick up the threads of whatever I was doing last..... starting on one box and resuming on the other.

I've learned that I could change the location of my "home" to another location but I don't really want to do that.  Too much hardware specific config stuff in the hidden . files on each computer is different.

Instead I'd like to change my "Desktop" on both boxes to the same folder on the network share (//Mini/Archive/John/Desktop) if possible.

Questions:

1. Possible?
2. How?
3. What is Ubuntu likely to do if I try to log in on Ubuntu on Max and the server can't be reached?

TIA

---

### Post by jpkotta on 2009-07-01
Assuming the network share is exactly what you want ~/Desktop to be, add this to /etc/fstab:
```
//server/share  /home/user/Desktop    cifs    defaults 0 0

```
This will mount the share at boot.  If the server isn't working for some reason, the mount will fail and you will get an error about it at boot time.  Anything you save to ~/Desktop will still be on the local disk, and will not be overwritten if the share is mounted later (it will be inaccessible until the share is unmounted).

If you need a password to mount the share, that can be done also.

---

