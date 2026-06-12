---
title: "can't delete contents of external media"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by shawnic on 2010-10-24
Whenever I try to delete files off of my flashdrive/ memory sticks, the files disappear but the amount of available space stays the same. the only way i've been able to actually clear them is by formatting.
What could be the problem?

---

### Post by ArgusVision on 2010-10-24
When you open it. press CTRL+H to see the hidden files. There's a file called .trash that needs to be cleaned out.

---

### Post by rampageoberon on 2010-10-24
Just to check - your're using the file manager to delete files. Tried emptying the trash as otherwise the files would be stored on the media.

also try removing from terminal as this will not go to trash store.

```
rm /path/to/file
```

---

### Post by SuaSwe on 2010-10-24
On my MP3 player and USB stick, the trash cans will only empty if I select to "safely remove" them (or equivalent on your distro - I'm on Maverick). Try that, if you haven't already?

---

