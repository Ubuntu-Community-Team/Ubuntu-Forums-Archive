---
title: "Script command not found"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by SpinningAround on 2010-05-18
Can't understand why this isn't working, what is wrong?

CODE:
```

#!/bin/bash
DATE=`date +%Y-%m-%d`

```
ERROR: (rough translation)
```
uptime.sh: row 2: date: command not found
```

```

:~$ ls -lahS /bin/bash
-rwxr-xr-x 1 root root 913K 2010-04-19 04:16 /bin/bash

```

```
:~$ ls -lahS uptime.sh 
-rwx------ 1 desktop desktop 59 2010-05-18 12:37 uptime.sh

```

---

### Post by CharlesA on 2010-05-18
Try adding the full path to date.

I ran into a similar problem a while ago, but fixed it somehow.

Fixed as in, I don't need to use the full path to each command now.

---

### Post by SpinningAround on 2010-05-18
Finally, found the problem. In an other part of the script did I change the $PATH value, then can't ubuntu actually search for commands.

---

