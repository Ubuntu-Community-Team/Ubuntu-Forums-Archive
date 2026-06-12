---
title: "Accidently deleted files...but didn't"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Warpnow on 2010-01-10
So I accidently hit delete on the wrong folder...it was 500gbs of files. I immediately powered down my computer...the hard drive space is not free on my computer...so the files are still somewhere I assume...not the trash, checked there...any ideas?

---

### Post by tom.swartz07 on 2010-01-10
> **Warpnow said:**
> So I accidently hit delete on the wrong folder...it was 500gbs of files. I immediately powered down my computer...the hard drive space is not free on my computer...so the files are still somewhere I assume...not the trash, checked there...any ideas?

Best bet: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Warpnow on 2010-01-11
I figured it out, and considering UFs insane google pagerank, I'll post the solution.

Files are stored in this folder during deletion:

home/username/.local/share/Trash/expunged

Each deletion has a number attatched, and a folder named that. I was able to simply copy them back into my home folder.

---

### Post by The Cog on 2010-01-11
> **Warpnow said:**
> Files are stored in this folder during deletion:

home/username/.local/share/Trash/expunged

Each deletion has a number attatched, and a folder named that. I was able to simply copy them back into my home folder.

Now, that is well worth knowing and remembering. Thanks for the tip.

---

### Post by gabo.cr on 2010-01-11
> home/username/.local/share/Trash/expunged

Very interesting !

---

