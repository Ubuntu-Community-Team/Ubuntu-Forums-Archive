---
title: "partitioning"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by bobheaps on 2010-03-09
a few weeks ago i purchased a notebook with windows7 pre installed. All the primary partitions were taken up, I deleted one which allowed me to install ubuntu 9.04. Everything worked well for a few weeks then the computer carried out  a check of the hard drive. it found errors which i allowed it to correct then it would not boot windows at all (i could still boot ubuntu) however to compound the problem i reinstalled windows from the recovery partition and this has screwed up my partitions, it put my /, /home, and swap artitions on an extended partition and it would not allow me to boot into ubuntu.
I have deleted all ntfs windows partitions but how do i get ubuntu to boot again? does it have to be on a primary partition and if it does how do i do it so?
could someone help me keeping the explanation understandable to a simple old man 

thanks

---

### Post by nothingspecial on 2010-03-09
I`m replying out of sympathy rather than knowledge. 

As far as I understand it, if you install windows, it overrides grub, which allows you to boot Ubuntu.

You need to install grub (or lilo) in order to access Ubuntu.

I know nothing of windows - so I could be wrong.

---

### Post by louieb on 2010-03-09
GRUB, Linux and Ubuntu can be installed in a primary or logical partition - makes not difference.

Need some information about the setup. Please follow the  [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file in your next post.

---

