---
title: "vi command problem"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by tsn30 on 2010-10-10
hi.

im doing an assignment for school. and the instructor told us to use the vi command to open the assignment.  the first time it works perfectly. but when exit. and try working on it some other time i come back and try vi assign1  to open the the assignment.
and it show me this message.

> 
Found a swap file by the name ".john.uli101.a1.details.gz.swp"
          owned by: john   dated: Thu Oct  7 14:28:23 2010
         file name: ~john/john.uli101.a1.details.gz
          modified: YES
         user name: john   host name: matrix
        process ID: 1572
While opening file "john.uli101.a1.details.gz"
             dated: Sun Oct 10 16:01:51 2010
      NEWER than swap file!

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r john.uli101.a1.details.gz"

    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file ".john.uli101.a1.details.gz
.swp"
    to avoid this message.  how do i stop that from occurring.

---

### Post by robsoles on 2010-10-10
Welcome to UF.

When you open a file using vi you must exit vi properly or it will leave a marker on your system as to what it was up to when you terminated vi using a less proper method.

```
:q
```
(press [Enter] after typing :q) is to quit vi if you haven't made any changes and you are not in an input mode (editing modes).
```
:q!
```
will 'force' quit vi, discarding changes if any have been made.
```
:wq
```
will save editing and close vi properly.

please look at ```
man vi
``` and [www.google.com/search?q=vi+commands](www.google.com/search?q=vi+commands)

---

### Post by tsn30 on 2010-10-10
thanks.  i havent been exiting properly i guess that was the problem.

---

