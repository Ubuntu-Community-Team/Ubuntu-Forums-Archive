---
title: "Any good Hex Editors?"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by Hovercat on 2009-10-16
I was wondering if anyone knew a hex editor for Ubuntu. I'm doing a school project, and I figured this would be useful. Please post links. .exe and .dll must be supported. Thanks in advance.

---

### Post by dearingj on 2009-10-16
I've GHex before; it's in Ubuntu's repositories, so you can install it the same way you install other programs in Ubuntu.
[http://directory.fsf.org/project/ghex/](http://directory.fsf.org/project/ghex/)

Are there any particular features you're looking for aside from editing exe and dll files?

---

### Post by Hovercat on 2009-10-16
No. I basically need it because I'm learning C++ and I figured it would eventually be useful.

---

### Post by Paresh on 2009-10-16
+1 for ghex

```
#!/bin/bash
# Load selected files in hex editor

IFS=$'\n'
for FILENAME in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
	# The & ensures that all selected files are loaded together
	ghex2 $FILENAME &
done

```

Put this in a script file and stick it in ~/.gnome2/nautilus-scripts.
and you can right click any file(s) to load it directly into ghex

---

### Post by Hovercat on 2009-10-19
Thanks. I'll give that a shot, I'm trying to hex edit a .dll for my Half-Life 2: Deathmatch servers. Also, I could also probably use it while learning C++.

---

