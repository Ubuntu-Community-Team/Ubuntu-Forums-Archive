---
title: "Speed up multiple file operations."
date: 2010-12-12
forum: New to Ubuntu
---

### Post by jalirious on 2010-12-12
Hi, my issue is that Ubuntu does not seem to handle multiple file transfer in an intelligent manner.

One ~700Mb file copied via USB; transfer time ~2 minutes.

While the first file is still copying, chose to copy a similar sized file at the same time.

Revised transfer time, ~4 minutes?

-> No, >25 minutes.

------------------------
The reason for this (I think) is the original 0.7 Gb file is written directly to RAM (1Gb), then via USB (fast). When two files are copying the combined file size is 1.4 Gb, which is then written directly to the USB ext. device, taking maybe 30x as long.

Can you, and if so how do you, set file operations to queue the file transfers and deal with them individually in sequence? 

Many thanks, Ben.

---

### Post by HermanAB on 2010-12-12
Howdy,

What you observed, is that once the RAM buffers are full, the transfer slows down to its true speed.  The bottle-neck is the PCI bus and USB controller.

If you want to measure the true speed, prepare a very large file of 10 GB and transfer that.  It is usually about 32 MBps, no matter what kind of computer you got.

---

### Post by jalirious on 2010-12-12
Hi Herman, thank you for your swift response.

Rather than gathering more accurate bench mark data, what I *want* is the ability to configure file operations so the subsequent file selected to copy only initiates copying following the successful completion of the file presently being copied.

Or, in a concession to brevity,

Make it copy one-at-a-time.

Do you know how to do that?

Regards, Ben.

---

