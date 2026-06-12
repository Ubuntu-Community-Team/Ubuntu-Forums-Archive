---
title: "use swap file instead of swap partition?"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by anon0 on 2009-02-03
How do you do this? And would this degrade performance? I figure this way you could put the file on say a RAID5 array and also save a partition.

---

### Post by rozbarwinek on 2009-02-03
> **anon0 said:**
> How do you do this? And would this degrade performance? I figure this way you could put the file on say a RAID5 array and also save a partition.

First question...
What for? having a swap partition is a good solution IMHO :P

---

### Post by kaibob on 2009-02-03
The following FAQ explains how to add a swap file:

[https://help.ubuntu.com/community/SwapFaq?](https://help.ubuntu.com/community/SwapFaq?)

I have never used a swap file and don't know if it degrades performance.

---

### Post by jimv on 2009-02-03
> **rozbarwinek said:**
> First question...
What for? having a swap partition is a good solution IMHO :P

So he doesn't have to have a partition, like he said.

---

### Post by Rolcol on 2009-02-03
A swap file should not cause a performance loss unless the file is vastly fragmented on the same individual drive.  The big benefit of a swap file (in my opinion) is that it's more manageable.  If, for example, you need more space, just increase the size of the file without having to shutdown to modify partitions.  I've read multiple times that the 2.6.* Linux kernels usually maintain the same performance between both methods.

Sample method of creating and using a swap file:

(The preceding hash (#) means that the command should be ran as root)

1) Create the file (2GB in this example):
```

# dd if=/dev/zero of=/swap bs=1024 count=2097152

```2) Make it usable as swap:
```

# mkswap /swap

```3) Edit fstab so it may be used on startup
```

# echo -e "/swap\tnone\tswap\tsw\t0 0" >> /etc/fstab

```4) Activate it for use immediately
```

# swapon -a

```

---

### Post by ronewolf on 2009-02-05
> **Rolcol said:**
> 

Sample method of creating and using a swap file:



Thank you for the clear step by step. Those steps worked fine and I now have a swap space as confirmed by swapon -s (and other). 

My specific goal in creating the space was to be able to hibernate. Is the hibernate command the best way to test this? If so, it looks like I have other problems with hibernate. 

Also, I was able to get the hibernate button to show up in the gnome power menu by checking can_hibernate in the gnome-power-manager general conf. But after trying to hibernate one time, the button is no longer present (even tho the option is still checked). WTH?

Anyway, I'll start a separate thread on these hibernate questions, mostly wanted to thank you for the clear info and procedure regarding creating a file swapspace.

---

