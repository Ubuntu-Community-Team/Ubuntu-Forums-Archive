---
title: "Copying files"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by helixed on 2009-03-07
Is there a way I can use the cp command or some other terminal command to delete any files at the destination which aren't present in the source?

Thanks,

helixed

---

### Post by Rolcol on 2009-03-07
rsync has features like that.  You may want to get started by looking at the manual page for it:
```
man rsync
```

---

### Post by ekaqu on 2009-03-07
> **helixed said:**
> Is there a way I can use the cp command or some other terminal command to delete any files at the destination which aren't present in the source?

Thanks,

helixed

So you have two folders, lets say ~/a and ~/b
You want to delete all the files in ~/b that are not in ~/a?

There is the easy --  but prob dont want to do -- way: 
```
rm ~/b/* ; cp ~/a/* ~/b/ 
```

the only other way I can think of would need a simple script to be written that would look up what files are in ~/a and get all files in ~/b that are not in there (grep -v) and use that to rm them.

---

### Post by Rolcol on 2009-03-07
> **ekaqu said:**
> So you have two folders, lets say ~/a and ~/b
You want to delete all the files in ~/b that are not in ~/a?

There is the easy --  but prob dont want to do -- way: 
```
rm ~/b/* ; cp ~/a/* ~/b/ 
```

the only other way I can think of would need a simple script to be written that would look up what files are in ~/a and get all files in ~/b that are not in there (grep -v) and use that to rm them.
That would take much longer as it would have to re-create the files it already has.  rsync copies files based on properties and you can add the --delete option to delete any files not in the first folder.  (Copying by properties allows rsync to skip files that are identical rather than overwriting them without need)

---

### Post by The Cog on 2009-03-07
rsync might be the answer. It normally copies any files that are different or missing in the destination, but with the --delete option it will also delete files in the destination that are absent in the source.

P.S.
I had the pleasure of having to restore about 50G from a backup today. I first just did it with **cp -a** but the backup drive conked out halfway through. After an fsck I tried again, using rsync this time. I was very surprised at the difference in noise the two made. cp had the disk heads rattling continuously (on the backup drive) whereas rsync hardly made a sound. I;m getting to like rsync.

---

### Post by helixed on 2009-03-09
Wow, thanks for the replies.  Rsync worked perfectly.

---

