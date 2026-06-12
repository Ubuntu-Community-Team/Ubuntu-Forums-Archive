---
title: "Hidden trash accumilating in pen os"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by nnjond on 2010-03-22
I,m taking a rest from a scrn res prob, (-which no one has been able to help me with-) by running my os from a pen where the prob doesn't appear.

However although there is loads of space on my pen, I keep getting infuriating warnings that i'm running out of space. This, it seem is because GNU/Linnux doesnt permanently delete all the trash, but keeps copies in .X folders somewhere. There must be a better way of deleting this trash other than firing up my hd os and deleting the .X's by  "Safely removing" the pen before re-booting?

Does anyone have an idea?

Thanks

---

### Post by patchwork on 2010-03-22
I haven't used the pen drive OS route, so bear with me.

In a standard install, you can navigate to ~/.local/share/Trash/files and delete the files in the Trash from there.  Can you do this from the pen drive as well?

Alternatively, you can set-up a cron job to empty the trash every so often; probably the best bet is to move the files in Trash to /dev/null (so long as you KNOW you won't need to recover them)

---

### Post by nnjond on 2010-03-22
Thanks for your tip. I found

/home/ubuntu/.local/share/Trash

But both folders are empty at the moment. Is there anywhere else where they might acrue?

---

### Post by patchwork on 2010-03-22
I don't know where else they would accrue using the live pen drive, maybe someone else knows?

---

