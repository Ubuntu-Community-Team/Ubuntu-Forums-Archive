---
title: "Create a partition without losing data"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by @rizz on 2010-04-07
Hi, 

   I have a 160gb hard drive with no partitions. Ubuntu runs on the entire disc.
I want to cut off 60gb from my file system with out losing the data that i already have on it.
I don't want to reinstall Ubuntu and cannot afford to lose all my data.
Is it possible to do so, without having to reinstall the OS.

I downloaded Gparted, whats next?:confused:

---

### Post by Paqman on 2010-04-07
You can't modify any partition while it's in use. So in order to shrink you main partition you'll have to boot up into the LiveCD and do it from there. Gparted is already on the LiveCD.

---

### Post by J V on 2010-04-07
> **@rizz said:**
> Hi, 

   I have a 160gb hard drive **with no partitions**. **Ubuntu runs on the entire disc**.
I want to cut off 60gb from my file system with out losing the data that i already have on it.
I don't want to reinstall Ubuntu and cannot afford to lose all my data.
Is it possible to do so, without having to reinstall the OS.

I downloaded Gparted, whats next?:confused:How can you run ubuntu without partitions? Please post the output of fdisk -l

---

### Post by tom.swartz07 on 2010-04-07
> **J V said:**
> How can you run ubuntu without partitions? Please post the output of fdisk -l

While youre at it, Back up your data. A bit external drive could be found for a low price at many different chain stores- Wal*Mart maybe?

I know it might be a bit of money, but the peace of mind in having your data securely backed up is well worth it.

---

### Post by @rizz on 2010-04-07
Can i use my Ubuntu cd as a live cd which i downloaded from the net to install ubuntu!

---

### Post by ajgreeny on 2010-04-07
> **@rizz said:**
> Can i use my Ubuntu cd as a live cd which i downloaded from the net to install ubuntu!
Yes, you can do that; it's probably what most people use.

If you let the installer do its job by default, when you installed Ubuntu, you will probably have three partitions that show in gparted
sda1-  the main OS partition.
sda2-  an extended partition.
sda5-  the swap partition which uses all of, and is shown to be inside sda2.

---

### Post by J V on 2010-04-07
What happened to 3 and 4?

Never done a default ubuntu install before hehe, always dual boot this, wubi that, seperate home partition etc...

---

### Post by mcduck on 2010-04-07
> **J V said:**
> What happened to 3 and 4?

Never done a default ubuntu install before hehe, always dual boot this, wubi that, seperate home partition etc...

partition numbers from 1 to 4 are for primary (or extended) partitions only, logical partitions will always start from 5.

---

### Post by J V on 2010-04-07
ah ok, makes sense... Wait, is the swap or the root logical?

---

### Post by mcduck on 2010-04-07
> **J V said:**
> ah ok, makes sense... Wait, is the swap or the root logical?

If I can remember right, the Ubuntu installer's automatic partitioning will put root on a primary partition, and then creates an extended partition and puts swap inside it (like in the setup ajgreeny posted).

So root is primary, and swap is logical.

---

### Post by @rizz on 2010-04-08
Thanks guys for all the replies.....

---

