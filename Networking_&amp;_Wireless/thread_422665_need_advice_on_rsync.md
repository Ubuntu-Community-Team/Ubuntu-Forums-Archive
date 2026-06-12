---
title: "need advice on rsync"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by josh on 2007-04-25
hello!

what rsync command would i use to backup a folder only when there are new files or files that has been changed. if nothing has changed in the files or no new files has been added to the folder, then i dont want rsync to do anything.

i currently use

```
rsync -avrzt /home/josh /home/storage
```

btw, i set it as an hourly cronjob.

thanks guys!

---

### Post by tgalati4 on 2007-04-25
Close.  -r and -t are redundant when you use -a.  -C will ignore untouched files.
Try rsync -Cavz
man rsync has several helpful examples.

---

### Post by jimbren on 2007-04-25
My understanding is that the job will run regardless of whether or not you make changes--rsync won't know if there are changes to the files until it looks at them.  But if there are no changes to the files, it should complete more or less instantly.  Is that not what you're seeing?

jimbo

---

### Post by josh on 2007-04-25
> **jimbren said:**
> My understanding is that the job will run regardless of whether or not you make changes--rsync won't know if there are changes to the files until it looks at them.  But if there are no changes to the files, it should complete more or less instantly.  Is that not what you're seeing?

jimbo

yup. it runs regardless. of course it will check it. i guess what i meant to say is that if there are not changes in the files or new additions to the folder, ignore and exit. i just dont want rsync copying the whole source directory again if i already have the contents in my storage. thank you!


tgalati4,
isnt the option -C only good if you have a filter list?  so in effect it should only copy new files and files that has changed in the source directory to my backup dir and ignore those that had no changes? thanks!

---

### Post by psusi on 2007-04-25
> **josh said:**
> yup. it runs regardless. of course it will check it. i guess what i meant to say is that if there are not changes in the files or new additions to the folder, ignore and exit. i just dont want rsync copying the whole source directory again if i already have the contents in my storage. thank you!


That is what rsync was made for, and that's what it does.  You don't have to do anything special.

---

### Post by josh on 2007-04-25
sweet! no more reading for me! thanks guys!

---

### Post by tgalati4 on 2007-04-26
You are correct.  I do a lot of music editing, and I normally exlude local cache files of work in progress.  These can be several hundred megs each.  No reason to back them up, since I only want final mixdowns saved.  Also check your internet cache files, they can get large, and no reason to back them up either.

---

