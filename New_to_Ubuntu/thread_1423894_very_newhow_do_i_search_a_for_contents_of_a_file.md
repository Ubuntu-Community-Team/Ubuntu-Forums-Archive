---
title: "very new/how do i search a for contents of a file?"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-03-07
I want to find a file somewhere in a directory and it has a specific string, how do i search based on matching the string in the contents of a file? (ie: not a filename search)

---

### Post by patchwork on 2010-03-07
cat "filename" | grep -il "string"


EDIT: forgot the -l

---

### Post by TurnOfTide on 2010-03-07
Rather, how can i recursively search a directory (since i don't know which file contains the string)?

---

### Post by patchwork on 2010-03-07
grep -irl "string" directory_name

---

### Post by donato roque on 2010-03-07
Have you considered index-based search?  If you're always trying to match a string search within files or metadata search then index-based search is very appropriate.
Try downloading Tracker or Beagle.  It's in the repositories.

---

