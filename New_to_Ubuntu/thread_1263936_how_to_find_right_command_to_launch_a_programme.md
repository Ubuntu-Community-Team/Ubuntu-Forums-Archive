---
title: "how to find right command to launch a programme"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by jessieros on 2009-09-11
I have been trying to work out which command will launch a programme in Ubuntu.
I can find the folder but don't know which file will cause the programme to start.
  Is there an equivalent of the Windows *.exe extension ?

---

### Post by Bachstelze on 2009-09-11
> **jessieros said:**
> Is there an equivalent of the Windows *.exe extension ?

No. In Linux, file extensions most of the time don't matter at all. An executable can have any extension, or even not have one at all, which is the most common case.

---

### Post by NoaHall on 2009-09-11
They are normally in either a directory called "bin" or "sbin"

---

### Post by Hospadar on 2009-09-11
The fact the the executable *does not* have an extension is typically the biggest hint.

Also executables tend to have simple names (which are therefore easy to remember and type in a terminal) and are usually named after the application.  For example the main executable for the gimp photo editor is simply: "gimp"

---

### Post by nhasian on 2009-09-11
it may help if you told us what you were trying to launch.  you could try the *whereis* command like:

```
whereis gcalctool
```

it will tell you that the program gcalctool is in /usr/bin/gcalctool

if you downloaded a program or script it will not run unless you make it executable.  you can right click on the item and tick the checkbox to make it executable in the properties, or from a terminal with:

```
chmod +x filename
```

---

