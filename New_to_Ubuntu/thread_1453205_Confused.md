---
title: "Confused"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by quista345 on 2010-04-12
What files match     [COLOR=#231F20][FONT=Arial] **$ **ls -l file[1-20][/FONT][/COLOR][COLOR=black][FONT=Arial][/FONT][/COLOR]

---

### Post by arvevans on 2010-04-12
The shell command "ls -l" lists all files (or a specific file if the name is given), and shows file parameters in long form...including:

[INDENT][LIST]
[*]Read-write-execute permissions for owner, group, and global users
[*]Ownership of the file
[*]File size in bytes
[*]Date last touched
[*]Time last touched
[*]Filename
[/LIST][/INDENT]

The manual page ('man ls') does not show any action for a trailing "[1-20]" and trying it gives an indication of "file not found" so it is apparently treated as if it were part of a filename.

---

### Post by WinterRain on 2010-04-12
> **quista345 said:**
> What files match     [COLOR=#231F20][FONT=Arial] **$ **ls -l file[1-20][/FONT][/COLOR][COLOR=black][FONT=Arial][/FONT][/COLOR]

It's just my opinion, but it seems you're just trying to push people at this point. Google may be a better ally.

---

