---
title: "Do I need a Swap Partition when  using Virtualization?"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by mikodo on 2010-01-17
Hello everyone,

I'm tired of worrying about Swap getting in the way of my Partition configuring. My system never seems to use it. I never use Suspend or Hibernation. I want to start using virtualization for testing newer/different OS's and releases of newer app's.

A screenshot of my system is included below:

Question:  Will having Swap be beneficial for my system with virtual tools like Virtual Box?

Thank you.

---

### Post by bodhi.zazen on 2010-01-17
One needs swap only if you run out of RAM or if you are using hibernation or suspend.

So long as you watch your memory usage with VBox you should be fine.

Swap does not improve performance.

---

### Post by blueshiftoverwatch on 2010-01-17
I set my swap to 10GB (2 more GB than I have RAM) and never seem to touch it. Back when I only had 4GB of RAM and was transferring 500GB worth of files from an external HD to an internal HD I used about 4GB of swap space. But I did the same after upgrading to 8GB of RAM and I don't think it even touched the swap space during very large file transfers.

---

### Post by mk1w86 on 2010-01-17
Although you could get away with not using swap I would personally recommend keeping the partition for system stabilities sake. ;)

---

### Post by mikodo on 2010-01-17
> **mk1w86 said:**
> Although you could get away with not using swap I would personally recommend keeping the partition for system stabilities sake. ;)

nuff said,

I'll keep it.

Thank you everyone.

---

