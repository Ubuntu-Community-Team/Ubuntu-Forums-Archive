---
title: "Disabling Ubuntu Files &amp; Folders Search"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by CrimsonTurkey on 2011-09-06
I was just wondering is there a way to disable the files & folders search in shortcut search I only what it to display programs that I have install not personal files and folders any help would be great thank you. :)

---

### Post by axatrikx on 2011-09-06
u can do it by disabling the file search lens in unity.
Go to unity places folder by
```
gksudo nautilus /usr/share/unity/places
```

You ll see the lenses, open files.place and add this line at the end.
```
ShowEntry=false

```
Restart Unity n log off n log back in.
If you want it back, just remove the added line.

---

### Post by CrimsonTurkey on 2011-09-06
I didn't seem to work anything else

---

