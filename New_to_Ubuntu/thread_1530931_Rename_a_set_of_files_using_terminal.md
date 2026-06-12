---
title: "Rename a set of files using terminal?"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-07-14
I've these images to be renamed:
[CENTER][SIZE=2][COLOR=Blue] 1024x768 - Wall 18.jpg 
1024x768 - Wall 24.jpg 
1024x768 - Wall 25.jpg 
1024x768 - Wall 27.jpg
1024x768 - Wall 32.jpg 
1024x768 - Wall 45.jpg[/COLOR][/SIZE]
[/CENTER]

rename to 
[CENTER]Wall 18.jpg
Wall 24.jpg
Wall 25.jpg
Wall 27.jpg
Wall 32.jpg
Wall 45.jpg

[LEFT]help me 
[/LEFT]
[/CENTER]

---

### Post by DaithiF on 2010-07-14
Hi,
use the **rename** command.
something like:
```
rename 's/^1024x768 - //' *.jpg
```

---

### Post by sisco311 on 2010-07-14
You could use the perl based rename command:
```
rename **-n** 's/^1024x768 - //' *.jpg
```

remove the **-n** option to actually rename the files.

or:
```
for file in *.jpg; do **echo** mv -b "${file}" "${file/1024x768 - /}"; done
```

remove the **echo** command to actually rename the files.

or try one of the GUI bulk renaming tools:
[list]
[*]thunar (file manager)
[*]gprename 
[*]purrr 
[*]pyrenamer 
[*]gwenrename 
[*]krename 
[/list]

---

### Post by MBG1987 on 2010-07-14
thanks to all of you

---

