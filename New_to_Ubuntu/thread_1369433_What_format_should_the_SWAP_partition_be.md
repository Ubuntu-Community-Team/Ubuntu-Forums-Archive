---
title: "What format should the SWAP partition be?"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by listerdl on 2010-01-01
Hi I am making a SWAP partition for ubuntu - which format should this be in? Ext3 or Ext4?

I am running with 9.10 and there is no partition for swap.

thanks :P

---

### Post by lisati on 2010-01-01
> **listerdl said:**
> Hi I am making a SWAP partition for ubuntu - which format should this be in? Ext3 or Ext4?

I am running with 9.10 and there is no partition for swap.

thanks :P

It should be linux-swap

---

### Post by championboxes on 2010-01-01
When partitioning with the live or alternate cd the format should say (linux swap) or something similar to that

---

### Post by listerdl on 2010-01-01
> **championboxes said:**
> When partitioning with the live or alternate cd the format should say (linux swap) or something similar to that

Absolutely - there is that option with GParted from the live CD so thats what I will do!

Thanks !

---

### Post by dwasifar on 2010-01-01
> **listerdl said:**
> Absolutely - there is that option with GParted from the live CD so thats what I will do!

Just so you know, if you haven't already done it yet: the way a swap partition gets set up during a default installation is a logical partition inside an extended partition.  

If you do a clean Ubuntu install, and allow the auto-partitioner to do its thing, you will wind up with /dev/sda1 formatted as ext4 for the main system, /dev/sda2 as an extended partition, and /dev/sda5 inside it formatted as linux-swap.  Your /etc/fstab file will then mount /dev/sda5 (not /dev/sda2) as your swap partition.

Not saying it *must* be this way, but if you keep it "stock" you'll have an easier time getting help in the forums if you have problems later.

---

