---
title: "NFS permission issues"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by dallingham on 2007-02-01
I have recently changed NFS and NIS servers (replacing a very old machine) for a small workgroup. Since the switch, we are having very strange permission issues. Files that should belong to me give me permission errors. 

[FONT="Courier New"]$ ls -ld firefox
drwx------ 3 dona vlsi 4096 2007-02-01 13:53 firefox
$ ls -ld firefox/*
ls: firefox/*: Permission denied
$ cd firefox
bash: cd: firefox: Permission denied
$ whoami
dona
[/FONT]

As you can see, I am the owner of the files, and I have read permission. A couple of minutes later, I can see the files:

[FONT="Courier New"]$ cd firefox
$ ls
8g3rtccm.default  pluginreg.dat  profiles.ini
$ ls -l
total 16
drwx------ 6 dona vlsi 4096 2007-02-01 14:29 8g3rtccm.default
-rw------- 1 dona vlsi 6651 2007-02-01 14:09 pluginreg.dat
-rw-r--r-- 1 dona vlsi   94 2007-02-01 13:34 profiles.ini
[/FONT]

Any ideas on what is happening?

---

### Post by dallingham on 2007-02-20
Fortunately, I got a response from the nfs mailing list. The problem can be resolved by adding the "no_subtree_check" option to the /etc/exports file.

/export *(rw,no_subtree_check,no_root_squash,sync)

---

### Post by thk on 2007-05-02
Thanks for the update. I was seeing the same thing. I've used NFS for many years and this is the first time I've ever had a problem.

---

