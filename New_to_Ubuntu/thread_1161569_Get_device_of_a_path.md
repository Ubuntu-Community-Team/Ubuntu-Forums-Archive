---
title: "Get device of a path"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by tnek on 2009-05-16
In my specific case I know that /home is on /dev/sda1 as I made the partitioning choice during installation:
```
kent@rat:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31a431a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14029   112687911   83  Linux
/dev/sda2           14030       14593     4530330    5  Extended
/dev/sda5           14030       14593     4530298+  82  Linux swap / Solaris
kent@rat:~$ ls -ld /home
drwxr-xr-x 3 root root 4096 2009-05-16 13:21 /home
kent@rat:~$ 

```

What I'm looking for is a method to locate on which **device** a certain **path** is located using the command line.

I'm going to use this method in a script I'm writing so it has to be *dynamic*.

Suggestions?

---

### Post by Rocket2DMn on 2009-05-16
```
mount
df -h
```
:)

---

### Post by Locutus_of_Borg on 2009-05-16
df -h /path/

---

### Post by theozzlives on 2009-05-16
> **tnek said:**
> In my specific case I know that /home is on /dev/sda1 as I made the partitioning choice during installation:
```
kent@rat:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31a431a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14029   112687911   83  Linux
/dev/sda2           14030       14593     4530330    5  Extended
/dev/sda5           14030       14593     4530298+  82  Linux swap / Solaris
kent@rat:~$ ls -ld /home
drwxr-xr-x 3 root root 4096 2009-05-16 13:21 /home
kent@rat:~$ 

```

What I'm looking for is a method to locate on which **device** a certain **path** is located using the command line.

I'm going to use this method in a script I'm writing so it has to be *dynamic*.

Suggestions?

Looks to me that everything is on sda1, except swap.

---

### Post by Rocket2DMn on 2009-05-16
> **Locutus_of_Borg said:**
> df -h /path/

Let's just do it all for him:
```
df /path/ | cut -d " " -f1
df /path/ | awk '{print $1}'
```

Heh.  :popcorn:

---

### Post by Locutus_of_Borg on 2009-05-16
if we're doing this much we might as well ssh into his box and...i dont know where i'm going with this but it sounds fun

---

### Post by Rocket2DMn on 2009-05-16
> **Locutus_of_Borg said:**
> if we're doing this much we might as well ssh into his box and...i dont know where i'm going with this but it sounds fun

That would not be secure of us.  However, I'm sure we could quickly turn this into a programming talk discussion, but I digress.  I think we have answered the question presented.

---

### Post by tnek on 2009-05-16
> **Locutus_of_Borg said:**
> df -h /path/
Thanks, that's what I needed.

> **theozzlives said:**
> Looks to me that everything is on sda1, except swap.
Yes, you didn't read the question. \\:D/

---

### Post by Miljet on 2009-05-16
I'm afraid that theozzlives did read your original post correctly. You stated that your /home was installed on sda1. That would infer to most people that your / was installed on another partition.

He was simply pointing that out.

---

### Post by tnek on 2009-05-18
> **Miljet said:**
> I'm afraid that theozzlives did read your original post correctly. You stated that your /home was installed on sda1. That would infer to most people that your / was installed on another partition.

He was simply pointing that out.
I'm afraid you didn't read it either: :D

> What I'm looking for is a method to locate on which **device** a certain **path** is located using the command line.

I'm going to use this method in a script I'm writing so it has to be *dynamic*.


The key word is dynamic. Anyway it's solved now.

---

