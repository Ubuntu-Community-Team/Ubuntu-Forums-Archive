---
title: "Installing EXT4 on new Hard Drive..pls help..."
date: 2009-03-28
forum: New to Ubuntu
---

### Post by hopelessone on 2009-03-28
Hi All,

Nice to see you all again...

In order to prep my HDD's for the new 9.04 i have a blank HDD and i wanted to format it to **EXT4** heres what i did:

> mkfs.ext4 /dev/sdd1
sudo tune2fs -m 0 /dev/sdd1
sudo mount -a
mount: unknown filesystem type 'ext4'
sudo tune2fs -E test_fs /dev/sdd1
sudo mount -t ext4dev /dev/sdd1 /mnt/hdd_3
sudo chown -R some:some /mnt/hdd_3

Can you please check my work, is it OK? Is this now **EXT4**?

my system:
8.10 2.6.27-11 generic

Now the **tune2fs -E test_fs** part is that OK? is there anything i have to do next month to change it back when 9.10 comes out?

Thanks...

---

### Post by mikewhatever on 2009-03-29
With a new HDD, why not use the partition manager provided with 9.04 at the time of installation? You really don't need preparing a month in advance.

---

### Post by HermanAB on 2009-03-29
Also, using Ext4 may not be a good idea.  It appears to be less robust than Ext3.  My favourites are IBM JFS and SGI XFS.

---

### Post by hopelessone on 2009-03-29
Oh...These HDD's are spare dives with *only* media on them...

is that an ok way to mount an newley created EXT4 system in 8.10?

> sudo tune2fs -E test_fs /dev/sdd1
sudo mount -t ext4dev /dev/sdd1 /mnt/hdd_3

What do the above commands do? I have 5 HDD's to process..

as you can see i get an error:

> sudo mount -a
mount: unknown filesystem type 'ext4'

if i try to mount my newly created EXT4 system in 8.10...

---

### Post by hyper_ch on 2009-03-29
I'd also advise not to use Ext4 yet. There are still some serious bugs that may result in a dataloss.

---

### Post by oldos2er on 2009-03-29
8.10 won't mount ext4 partitions, as you noticed. You would need to compile a 2.6.28.x kernel for it, or use a 9.04 kernel.

---

### Post by sdennie on 2009-03-29
Do not, under any circumstances, use ext4 under Intrepid.  It's not considered stable in the 2.6.27 kernel and, from experience, I can say that it's not stable in 2.6.28+ (and in fact regressing quite rapidly as the bug patches start causing HUGE amounts of latency).  If you switch to ext4dev for a media drive in Intrepid, you can expect to maybe not be able to change to ext4 (proper) in Jaunty.  And, if you can, you can expect the latency added for bug fixes to make it not feasible to actually use your media.

I was a huge supporter of ext4 when 2.6.28 came out.  I recently switched back to ext3 because, as kernels progressed, the filesystem became less and less usable.  Specifically for media.  Unless you don't mind latency in the 200ms range for operations that never had that in ext3.

---

### Post by hopelessone on 2009-03-29
Ah ...OK many thanks for all the info..
Most helpful..:P

---

