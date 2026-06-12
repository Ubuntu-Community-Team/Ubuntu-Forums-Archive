---
title: "Manually Create Partition For Ubuntu"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by EpikRageQuit on 2010-10-16
I want to create a partition to install ubuntu on. I am doing this for my laptop, so I have a dual boot. I resized the windows partitions and deleted one so I could create the most room for Ubuntu. The screenshot below shows the settings I THINK are proper for what I am doing. I am just asking for approval of someone with more experience.


THANKS

---

### Post by sandyd on 2010-10-16
> **EpikRageQuit said:**
> I want to create a partition to install ubuntu on. I am doing this for my laptop, so I have a dual boot. I resized the windows partitions and deleted one so I could create the most room for Ubuntu. The screenshot below shows the settings I THINK are proper for what I am doing. I am just asking for approval of someone with more experience.


THANKS
how much RAM do you have?
If you have enough, you don't need a swap file.
however, if you want to hibernate, you have to have one.
typically, if you want to hibernate, the swap space must be as large as your RAM
so, if you have 2GB ram, do 221694 (subtract it properly, don't use what  I just did)(1GB = 1024mb) for the current partition your about to create and 2000 for  the swap partition.

However, if you don't need to hibernate, but still want to have swap  space (swap space is sorta like the windows paging file), I would  reccomend using 1GB swap.

Therefore, the size of the partiton you would create in that case would be 222694mb
and create a swap using the 1GB free space thats left.

and you can ignore everything I said, and click "ok" if you don't need a swap file

---

### Post by btindie on 2010-10-16
That will give you one partition to use as your 'root' partition. You won't have a partition to use as 'swap' - similar to windows' pagefile, under Linux this is used for hibernate and should be slightly bigger than your RAM. You may also want a separate partition to use for your /home directory, you can then create that as an encrypted partition if you like.

Usually you'd have two partitions - one for the 'root' file system and the other for 'swap'. If you've got ample RAM, maybe as low as 1GB depending on usage ideally 2GB, you can do without swap if you don't want to hibernate.

---

### Post by EpikRageQuit on 2010-10-16
> **btindie said:**
> That will give you one partition to use as your 'root' partition. You won't have a partition to use as 'swap' - similar to windows' pagefile, under Linux this is used for hibernate and should be slightly bigger than your RAM. You may also want a separate partition to use for your /home directory, you can then create that as an encrypted partition if you like.

Usually you'd have two partitions - one for the 'root' file system and the other for 'swap'. If you've got ample RAM, maybe as low as 1GB depending on usage ideally 2GB, you can do without swap if you don't want to hibernate.

Okay, don't know about swap thing but i don't think I need to hibernate so thanks guys :)

---

