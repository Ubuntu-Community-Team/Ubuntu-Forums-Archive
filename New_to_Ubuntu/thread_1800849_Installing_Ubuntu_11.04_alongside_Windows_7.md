---
title: "Installing Ubuntu 11.04 alongside Windows 7"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by ekendra7 on 2011-07-09
Okay friends, it is 3am in the morning, and still can't install Ubuntu in my laptop - tried for 17 times by now. I am a basic user of Ubuntu. Well, here goes my scenario.

In the Dell Vostro 3400, my HDD is partitioned as 100MB (system), 120GB (Windows7 NTFS), 120BG (General, NTFS), and the remaining 30GB (already partitioned in ext4 for installing Ubuntu) - approx size.

I want to install Ubuntu in the last 30 GB portion of the HDD which has the file format ext4. But, it doesn't allow me to install. Anything wrong?

Since I'm a beginner, where can I find basic installation video of Ubuntu 11.04 (latest version plz)?

---

### Post by spiky001 on 2011-07-09
Have a look [COLOR=Red][here]("http://www.psychocats.net/ubuntu/installing")[/COLOR] you need to select the 3rd option that will allow you to install to different partitions

---

### Post by Quackers on 2011-07-09
Or delete the 30GB ext4 partition and select the "install alongside" option in the installer.

---

### Post by centaurusa on 2011-07-09
Take a look at:

[http://linuxnorth.wordpress.com/manual-partitioning/](http://linuxnorth.wordpress.com/manual-partitioning/)

It has some basic information on manual partitioning, plus links to related video tutorials.  Other posts and tips in the same blog talk about installing Ubuntu in a dual-boot configuration.  While these are mainly aimed at Version 10.04 LTS (Lucid Lynx), a long-term support release, they also apply to Ubuntu versions in general.

---

### Post by Jacobonbuntu on 2011-07-09
> **ekendra7 said:**
> Okay friends, it is 3am in the morning, and still can't install Ubuntu in my laptop - tried for 17 times by now. I am a basic user of Ubuntu. Well, here goes my scenario.

In the Dell Vostro 3400, my HDD is partitioned as 100MB (system), 120GB (Windows7 NTFS), 120BG (General, NTFS), and the remaining 30GB (already partitioned in ext4 for installing Ubuntu) - approx size.

I want to install Ubuntu in the last 30 GB portion of the HDD which has the file format ext4. But, it doesn't allow me to install. Anything wrong?

Since I'm a beginner, where can I find basic installation video of Ubuntu 11.04 (latest version plz)?


--- forgive me the simpleness of my question, but you may have forgotten the SWAP partition...?

(you'll probably be asleep, as it is 4 am for you now :-$)

---

### Post by wildmanne39 on 2011-07-09
> **ekendra7 said:**
> Okay friends, it is 3am in the morning, and still can't install Ubuntu in my laptop - tried for 17 times by now. I am a basic user of Ubuntu. Well, here goes my scenario.

In the Dell Vostro 3400, my HDD is partitioned as 100MB (system), 120GB (Windows7 NTFS), 120BG (General, NTFS), and the remaining 30GB (already partitioned in ext4 for installing Ubuntu) - approx size.

I want to install Ubuntu in the last 30 GB portion of the HDD which has the file format ext4. But, it doesn't allow me to install. Anything wrong?

Since I'm a beginner, where can I find basic installation video of Ubuntu 11.04 (latest version plz)?Hi, is it possible you have left out a partition? like recovery partition if so then you may have 4 primary partitions already, and that is as many as you can have, in that case you would have to delete a partition but do not do that without posting the results of this command from a terminal.
```
sudo fdisk -lu
```

---

