---
title: "How to make a Script to Copy/Modify/Move file"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by mpurses on 2009-05-06
I need to make a script to:

1. Copy file A to Location B.
2. Open file A.
3. Do a "Find and Replace All" for a certain phrase.
4. Save File A.

How could i do this in one command line script?

---

### Post by Penguin Guy on 2009-05-06
Try looking into the [COLOR=Green]sed[/COLOR] command.

---

### Post by mpurses on 2009-05-06
is this close?

```
sed 's/oldstuff/newstuff/g' /LOCATION/OF/ORIGINAL/FILE > /DESTINATION/OF/MODIFIED/FILE
```

---

### Post by slakkie on 2009-05-06
Yes, very close, it does the trick just like you want to :).

sed -i.bak 's/stuff/other stuff/g' $file will replace $file and keeps a backup named $file.bak.

---

