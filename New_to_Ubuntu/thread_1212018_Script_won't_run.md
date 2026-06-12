---
title: "Script won't run"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by ncc1701e on 2009-07-13
I have written a shell script which executes a bunch of commands including launching an executable in my home directory. So the script looks something like

____________________________________________
#! /bin/sh
command 1
command 2
/home/myhomdirectory/subdirectory/subdirectory/executable -arg1 -arg2 &
Launch Program of Interest
undo command 2
undo command 1
killall -9 executable
____________________________________________

However, the command containing the executable doesn't take effect. If I paste this command alone in to a terminal it works fine. The rest of the scrip seems to run fine.

---

### Post by keplerspeed on 2009-07-13
Add:

```

#! /bin/bash

```

At the start of the script and also chmod the script to make it executible.

---

### Post by frunns on 2009-07-13
> **keplerspeed said:**
> Add:

```

#! /bin/bash

```

At the start of the script and also chmod the script to make it executible.

He already has
```

# /bin/sh

```

Don't know if the exclamation mark makes a difference, add it or replace with 
```
#! /bin/bash
```

---

### Post by ncc1701e on 2009-07-13
oops sorry i actually do have the exclamation in my script I just forgot to type it here I was typing by hand and not pasting. I have edited my original post to reflect this now.

thanks

---

### Post by keplerspeed on 2009-07-13
Have a look here:

[http://tldp.org/LDP/abs/html/sha-bang.html](http://tldp.org/LDP/abs/html/sha-bang.html)

> The  sha-bang  ( #!) [1]  at the head of a script tells your system that this file is a set of commands to be fed to the command interpreter indicated. The #! is actually a two-byte [2]  magic number, a special marker that designates a file type, or in this case an executable shell script (type man magic for more details on this fascinating topic). Immediately following the sha-bang is a path name. This is the path to the program that interprets the commands in the script, whether it be a shell, a programming language, or a utility. This command interpreter then executes the commands in the script, starting at the top (the line following the sha-bang line), and ignoring comments. [3]

---

### Post by Keith Hedger on 2009-07-13
You should not have a space between the exclamation mark and the path, so:
"#!/bin/bash" NOT "#! /bin/bash" (without the quotes!)

---

