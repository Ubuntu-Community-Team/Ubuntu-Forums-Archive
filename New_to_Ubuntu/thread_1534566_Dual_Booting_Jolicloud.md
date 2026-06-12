---
title: "Dual Booting Jolicloud?"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-07-19
Hello, I currently have Ubuntu 10.04 (normal version) on my netbook.  I would like to dual-boot with Jolicloud.  Attached is how my disk is currently partitioned.  If possible, could somebody give me a step by step guide on crating a new partition, installing Jolicloud, and how to share the /home folder between the two OSs?  Like if I save something on Jolicloud it will be available on Ubuntu in the same place.

---

### Post by moore.bryan on 2010-07-19
> **TriBlox6432 said:**
> Hello, I currently have Ubuntu 10.04 (normal version) on my netbook.  I would like to dual-boot with Jolicloud.  Attached is how my disk is currently partitioned.
Sorry, but nothing's attached.

> If possible, could somebody give me a step by step guide on crating a new partition, installing Jolicloud, and how to share the /home folder between the two OSs?  Like if I save something on Jolicloud it will be available on Ubuntu in the same place.
Sharing the home folder, although technically *possible*, is an **horrifically** bad idea. Trust me on this one; I'm speaking from experience. A better way to do it is to have one partition for sharing between all your distros and link folders into your home partition.
When you install Jolicloud, you should be able to create some new partitions, but without knowing how you already have things set-up I can't necessarily provide a "do this" guide.
So... how's it set-up?

---

### Post by TriBlox6432 on 2010-07-19
Sorry about that.  Here's the attachment.

---

### Post by moore.bryan on 2010-07-20
Okay... this is how **I** would do it, but suggest you ask any questions before you dive-off into the deep end.

You need to first download [GParted Live]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.5.2-9/gparted-live-0.5.2-9.iso/download") iso, either to burn onto a cd or copy to a usb. All of the following [b]must[b] be done from within that and not from within your Ubuntu install! If you don't know how to make a bootable usb, let me know.

Next, I would *keep* your root (sda1) as-is at 10gb, *resize* your home (sda2) to 10gb, *create* two new ext4 partitions (each 10gb) and a large ext4 partition that takes-up the rest of the empty space. Basically, gparted would *probably* make it look like this:
```
/dev/sda1 - 10gb - Ubuntu - /
/dev/sda2 - 10gb - Ubuntu - /home
/dev/sda3 - 4gb   - Extended
     /dev/sda5 - 4gb - Swap
/dev/sda4 - 10gb - Eventual Jolicloud /
/dev/sda6 - 10gb - Eventual Jolicloud /home
/dev/sda7 - 105.05gb - Shared storage

```

The logic here is by having shared storage as a separate partition, all your installed distros can use it and you can simlink any folders you create in it to those in your /home, basically sharing home folders across distros.

Then, when you install Jolicloud, you'll select the manual partitioner and tell it to put Jolicloud's root in whatever gparted names the one 10gb partititon (/dev/sda4 in the example above) and Jolicloud's home in the other 10gb partitition (/dev/sda6 in the example above).

I don't think I left anything out, but ask away!

---

### Post by mikechant on 2010-07-20
bryan,
I don't know if I'm just misunderstanding but your suggested partition layout seems to have more than the maximum of four primary partitions. If you want more than four partitions you would have three normal primary partitions and one extended primary partition containing all the remaining partitions as logical partitions, for example
```
/dev/sda1 - 10gb - Ubuntu - /
/dev/sda2 - 10gb - Ubuntu - /home
/dev/sda3 - 24gb   - Extended, containing sda5,6,7
     /dev/sda5 - 4gb - Swap
     /dev/sda6 - 10gb - Eventual Jolicloud /
     /dev/sda7 - 10gb - Eventual Jolicloud /home
/dev/sda4 - 105.05gb - Shared storage
```

---

### Post by moore.bryan on 2010-07-20
Thanks, mikechant... I just looked at my own and realized I was using logical partitions. Never heard of a "maximum" for primary partitions, though. That's an interesting tidbit of info...

From a perfect-world standpoint, I would completely reinstall and see
```

/dev/sda1 - swap - 2gb
/dev/sda2 - extended
     /dev/sda5 - Ubuntu / - 10gb
     /dev/sda6 - Ubuntu /home - 10gb
     /dev/sda7 - Jolicloud / - 10gb
     /dev/sda8 - Jolicloud /home - 10gb
     /dev/sda9 - ext4 storage - remainder

```

---

### Post by TriBlox6432 on 2010-07-20
I would love to reinstall, but I can't.  Ubuntu uses a special driver for my netbook's wireless, and I can only download it through a wired connection, and my home internet is down and I can only use the wifi at library or starbucks.

---

### Post by moore.bryan on 2010-07-20
I didn't mean to give you the impression you *should* reinstall; that's just the perfect world situation, IMHO.

You still need to get your hands on the GParted Live USB or CD and change some sizes. Reassessing your situation, I'd probably shrink your /home to 10gb and then turn the extra space into a logical partition, splitting it up like before.

---

### Post by TriBlox6432 on 2010-07-27
Alright, thanks.  I installed jolicloud and didn't really like it after a few days, so back to Ubuntu.  :D

---

