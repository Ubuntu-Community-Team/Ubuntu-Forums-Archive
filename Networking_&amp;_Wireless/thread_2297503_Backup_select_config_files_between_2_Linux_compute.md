---
title: "Backup select config files between 2 Linux computers."
date: 2015-10-04
forum: Networking &amp; Wireless
---

### Post by Rytron on 2015-10-04
Hi to all at UF.

I want to sync only these directories between my #1PC and #2PC. I want it to delete files on #2PC that are different on #1PC.

These are the directories:
.mozilla
.thunderbird
.config/chromium

Would a simple bash script be best?

The LAN IP address for #2PC is: 192.168.1.11

Thanks.

---

### Post by TheFu on 2015-10-05
If you have a master - use rsync.  1 line is all you need.  Of course, you'll want to configure both for ssh use. rsync uses ssh by default.

---

### Post by Rytron on 2015-10-05
> **TheFu said:**
> If you have a master - use rsync.  1 line is all you need.  Of course, you'll want to configure both for ssh use. rsync uses ssh by default.

Hi TheFu.

SSH is good on both computers. What command line will I use?

---

### Post by TheFu on 2015-10-05
Hope you don't mind the "teaching you to fish" method.  [https://rsync.samba.org/examples.html](https://rsync.samba.org/examples.html) has examples, like what you need.  

If you are stuck, post the cmd attempted. The attempt is important to me, because doing it for you doesn't lead to learning the skill. Teaching you to do it yourself is "mentoring."  rsync is one of the most amazing SW tools ever created and I believe an important skill for every Unix user to know, if only for the simplest uses.

---

### Post by Rytron on 2015-10-06
> **TheFu said:**
> Hope you don't mind the "teaching you to fish" method.  [https://rsync.samba.org/examples.html](https://rsync.samba.org/examples.html) has examples, like what you need.  

If you are stuck, post what was attempted. The attempt is important to me.

Ok. :mrgreen:

I may also try LuckyBackup.

Cheers Mr Fu.

---

### Post by TheFu on 2015-10-06
> **Rytron said:**
> Ok. :mrgreen:

I may also try LuckyBackup.

Cheers Mr Fu.

There are 50 ways to get this working. ;) tar, star, gnutar, zip, bzip, ...  could also be used - but all of those are multi-step, unlike rsync.  There is a GUI for rsync - grsync, but scripting that to update things daily, weekly, monthly ... GUIs don't script very well, if at all.

---

### Post by Rytron on 2015-10-06
> **TheFu said:**
> There are 50 ways to get this working. ;) tar, star, gnutar, zip, bzip, ...  could also be used - but all of those are multi-step, unlike rsync.  There is a GUI for rsync - grsync, but scripting that to update things daily, weekly, monthly ... GUIs don't script very well, if at all.

I would run this manually.

---

### Post by Rytron on 2015-10-09
I've got this so far. It tries to delete other dot config folders on PC#2.

```
rsync -h --progress --stats -r --delete-after --include=.mozilla --include=.thunderbird --include=*/ --exclude=* --prune-empty-dirs /home/roy/ roy@192.168.1.11:/home/roy/
```

I really don't fancy spending hours on this.

I might just stick to manually deleting on PC#2 and copying the newer folders via sftp://roy@192.168.1.11/home in 2 open file manager windows.

---

