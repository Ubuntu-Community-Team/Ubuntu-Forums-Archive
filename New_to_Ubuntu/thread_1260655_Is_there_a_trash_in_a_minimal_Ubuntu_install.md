---
title: "Is there a trash in a minimal Ubuntu install?"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-09-07
Hello,

I did a minimal Ubuntu install (8.04) using openbox as my window manager. Now I was wondering when I delete a file in openbox, is it lost or does it go to a trash folder? If it does, where is that folder?

Thanks!

---

### Post by yabbadabbadont on 2009-09-07
It depends... what method did you use to delete the file(s)?

---

### Post by sylvainrb on 2009-09-07
> **yabbadabbadont said:**
> It depends... what method did you use to delete the file(s)?

The delete key on the keyboard or the delete option in PCMan-FM (file manager).

If you use rm command in the terminal, files are gone for good, correct?

---

### Post by credobyte on 2009-09-07
```
~/.local/share/Trash/files

```

---

### Post by sylvainrb on 2009-09-07
> **credobyte said:**
> ```
~/.local/share/Trash/files

```

~/.local/share/Trash/ directory doesn't not exist.

---

### Post by yabbadabbadont on 2009-09-07
> **sylvainrb said:**
> The delete key on the keyboard or the delete option in PCMan-FM (file manager).

If you use rm command in the terminal, files are gone for good, correct?

Yes, if you use the rm command, they are immediately removed and gone for good.

Deleting them from pcmanfm may, or may not, have moved them to the trash.  It depends upon how you have pcmanfm configured.  Check the settings.  There is an option that decides whether or not files are immediately deleted or moved to the trash.

---

### Post by sylvainrb on 2009-09-07
> **yabbadabbadont said:**
> Yes, if you use the rm command, they are immediately removed and gone for good.

Deleting them from pcmanfm may, or may not, have moved them to the trash.  It depends upon how you have pcmanfm configured.  Check the settings.  There is an option that decides whether or not files are immediately deleted or moved to the trash.

Thanks! That's what I thought, but there's no such option in PCMan-FM!

---

### Post by sylvainrb on 2009-09-07
Lol forgot to mention: when I delete using PCMan-FM it asks if I really want to delete the files... (Does that mean they're gone then?)

---

### Post by yabbadabbadont on 2009-09-07
Hmmm, I installed it to test and I see that you are correct...  I could have sworn that I saw such an option before.  Maybe I was using a different version than the one in the repositories.

I would guess that the files are really gone.

EDIT: Yep, they are gone.  See the "Issues" section here for details: [http://wiki.lxde.org/en/PCManFM](http://wiki.lxde.org/en/PCManFM)

---

### Post by sylvainrb on 2009-09-09
> **yabbadabbadont said:**
> Hmmm, I installed it to test and I see that you are correct...  I could have sworn that I saw such an option before.  Maybe I was using a different version than the one in the repositories.

I would guess that the files are really gone.

EDIT: Yep, they are gone.  See the "Issues" section here for details: [http://wiki.lxde.org/en/PCManFM](http://wiki.lxde.org/en/PCManFM)

Ok got it thanks! I realized it after searching the whole system. Deleted a file for test and tried to look for it haha!

---

