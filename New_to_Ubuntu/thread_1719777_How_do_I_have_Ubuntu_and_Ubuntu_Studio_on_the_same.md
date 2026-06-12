---
title: "How do I have Ubuntu and Ubuntu Studio on the same machine?"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by Mike1962 on 2011-04-02
Hi,
I'd like to run Ubuntu Studio along side Ubuntu so I can have the real time kernel for recording and the normal kernel for every day work.

I presume it's straight forwards but any advice from anyone who has done it would be great.
Mike

---

### Post by fabricator4 on 2011-04-02
> **Mike1962 said:**
> Hi,
I'd like to run Ubuntu Studio along side Ubuntu so I can have the real time kernel for recording and the normal kernel for every day work.

I presume it's straight forwards but any advice from anyone who has done it would be great.
Mike

Not Ubuntu Studio, but I have two releases on this machine, Lucid and Natty beta 1.

It's best to have three partitions plus a swap partition.  I set up two partitions of about 20+ GB each for the two file systems / (root) and most of the rest of the disk (less the swap partition) for /home.

When you install the OS select manual partitioning and specify which 20 GB partition you want as the file system / (root) and specify the large remainder as /home.  Repeat for the second release.  Note that you specify the same partition for /home both times, which means that your home directory will be the same for both releases.  If you specify the same username for both installations your data and settings will be identical for both also.

To state the obvious: When data already existed on the /home partition, make sure that you do not tell the installer to format it. You just want the installer to set up fstab so it gets mounted as /home

Do not neglect to set up your swap partition which should probably be at least as large as your RAM size.

I prefer to run Gparted off the LiveCD (or the Gparted boot CD) to do the partitioning first before I do the installation.

You can set up the first 20 GB partion as the primary partition while all the rest must be on an extended partition.

There's been some good installation instructions written that cover this topic of doing multiple installs. You might want to do a search and read some of them also if you need more detail.

Chris.

---

### Post by wojox on 2011-04-02
I would install Ubuntu Studio and two kernels. It would cut down on redundancy.

---

### Post by JOHNNYG713 on 2011-04-02
Simply open synaptic search Ubuntu studio and install the packages, Note this will take some time, Boom now you have Your ubuntu, running ubuntu studio ! :guitar:

---

### Post by Mike1962 on 2011-04-26
Thanks guys, sorry for taking so long to get back, been away!

---

