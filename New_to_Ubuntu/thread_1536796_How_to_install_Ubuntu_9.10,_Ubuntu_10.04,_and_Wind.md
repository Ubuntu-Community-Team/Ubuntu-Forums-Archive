---
title: "How to install Ubuntu 9.10, Ubuntu 10.04, and Windows XP"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by lbrty on 2010-07-22
I'm already dual booting Ubuntu 10.04 and Windows XP and was interested in installing Ubuntu 9.10 along side those two. Is this possible? Thanks!

---

### Post by jtarin on 2010-07-22
Of course it's possible if you prepare a partition for it. Are you using [Grub2]("http://www.dedoimedo.com/computers/grub-2.html#mozTocId835620") to load both operating systems? Then it's possible to use your existing Grub2 and configure it for your new OS.Follow the link I have inserted and read how to configure Grub2, pay particular attention to the section "OS Prober" to detect your new OS.

---

### Post by anon.jdh on 2010-07-22
Just back up your data first (this should go without saying).

If you have one disk you will have to re-size a partition to have any effective space for the O.S.

Use GParted and re-size the space you need.
With that freshly free space:
Create a Partition (should be at least 8GB) and format it as ext3/ext4 (I prefer ext3).
Select to format and install in that space.

Hope that helps.

---

### Post by lbrty on 2010-07-24
Thank you everyone!

---

