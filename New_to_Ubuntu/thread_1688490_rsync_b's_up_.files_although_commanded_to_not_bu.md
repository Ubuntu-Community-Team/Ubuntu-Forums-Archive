---
title: "rsync b's up .files although commanded to not bu"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-02-15
I ran rsync today as:

rsync -avz --delete --exclude=".*/" /home/mark/ /media/TV/backup

bu of 15-feb-2011 returned:

sent 18873139008 bytes  received 1644301 bytes  8558051.83 bytes/sec
total size is 20221841756  speedup is 1.07
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

On looking in /media/TV/backup (folder where the dirs/files are) I see that ALL the hidden . files are there. Is this due to the wrong quotation mark? Or some other more sinister problem? It even backed up the .gvfs which makes me think the bu is probably corrupted and cannot be used for a restore.

===============
An hour later.

I was seeing the hidden dot folders as I had not deleted them using sudo/gksudo. Once they are deleted the BU using --exclude worked, and rsync reported no errors.

---

