---
title: "purpose of /boot partition"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by bnhrobotics on 2009-11-07
Hello,

I am about to make a 9.10 server (mostly for web serving purposes). I read some about creating a separate /boot partition. What is the purpose of this? What size should it be?

My thoughts were currently to have these partitions.

/
/boot (maybe?)
/swap
/var/www (or maybe /srv where I can point to the things I am serving. any thoughts here?)
extra space for other partitions?

Thanks

---

### Post by falconindy on 2009-11-07
Typically, the purpose of a separate boot partition is to allow GRUB to boot  off of something it can understand, as opposed to something more exotic, such as an LVM partitioned MDADM (software raid) array. Normally, this partition is no bigger than 50-100mb, depending on how many kernels you plan on keeping around.

The /srv directory is typically where directories are mounted via a bind. You wouldn't put the actual content there.

Break up your hard drives into partitions based on what you're serving. Essentially you want to separate, physically if possible, the OS from the data.

---

### Post by bnhrobotics on 2009-11-07
Thanks for the advice. My desktop does not have its own /boot partition. I think I still fail to see why GRUB would prefer its own partition.

So if I am doing a web server, and maybe a file server and possible SVN server, what partitions should I make for those?

Thanks

---

### Post by falconindy on 2009-11-07
> **bnhrobotics said:**
> Thanks for the advice. My desktop does not have its own /boot partition. I think I still fail to see why GRUB would prefer its own partition.

So if I am doing a web server, and maybe a file server and possible SVN server, what partitions should I make for those?

Thanks
It's not a matter of preference. Grub is **unable** to boot off an LVM partitioned MDADM array (and I have my doubts about Grub2). If you have a setup like this, you **must** have /boot on a separate partition or you're not going to get anywhere.

/var sounds like a good choice to partition separately for hosting both SVN and WWW.

---

### Post by louieb on 2009-11-07
For a normal desktop install I can think of only one reason to ever use a separate partition for /boot - GRUB error 18 - its a workaround for limitations found in the BIOS of older PCs.

There are a couple of special install types that would required a separate /boot partition - an encrypted install  (GRUB doesn't encrypt/decrypt)  and the use of LVM come to mind.   

I normally like to use two partitions one for the OS - 20GB or so, and another for my data - as large as I can make it.

---

