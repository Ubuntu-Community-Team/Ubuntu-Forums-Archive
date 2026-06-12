---
title: "Backing up Programs, System Settings, and Home Dir"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by apb2390 on 2009-09-27
Hi all,
Yeah. the title explains it nicely. I want to back up both my Home directory and my programs. I want the programs to be in a separate backup and (if possible) to be executable AFTER a clean install and backup. I would like my system settings to be backed up so that they can be restored and work real quickly. And i can figure out my home directory.  And I want to do it all onto an external HDD.

Did you catch all that? Good. Thanks in advance.

---

### Post by kendoori on 2009-09-27
I was a little freaked out by it at first, but I've settled on [Clonezilla]("http://clonezilla.org/"). I had a bit of a disastor last month, and quickly restored my entire system the next day. I store my backups on my home network, but you can just as easily store everything on an external USB drive or another partition. I bought a cheap USB thumb drive I've made into a bootable Clonezilla.

[This]("http://www.howtoforge.com/back-up-restore-hard-drives-and-partitions-with-clonezilla-live") is a good step by step that will walk you through what you want to do.

---

### Post by apb2390 on 2009-09-27
Thank you kendoori. This looks like an excellent program and tutorial. I think it'll turn out perfect.

---

### Post by nhasian on 2009-09-27
+1 for clonezilla

I just keep my root, /home, and /data partitions separate.  I backup my partitions regularly and if something breaks I can quickly restore in like 5 mins with Clonezilla.  its saved my butt several times since I'm testing the development version of Ubuntu.

---

