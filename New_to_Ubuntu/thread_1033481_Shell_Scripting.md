---
title: "Shell Scripting"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by ebubar@gmail.com on 2009-01-07
I have a question on shell scripting.  I need to run a script to;
1) open a fortran program, lets call it PROGRAM
- I can do this no problem
2) This program reads in an input file, lets call it INPUT
   When it runs it prompts the user for the name of the input file.
   This file will have the same name every time.  How can I send this
   filename so the PROGRAM will recognize the filename INPUT

Thanks for any help

---

### Post by cmnorton on 2009-01-07
-------------------- begin TEST shell script --------------------

#!/bin/bash
# test shell script for launching a Fortran program

/full-path/fortran_program INPUT

-------------------- end TEST shell script ------------------------

Suggest you get one of umpteen books on Linux shell scripting. I explicitly use #!/bin/bash instead of #!/bin/sh because /bin/sh is a symbolic link to /bin/dash which does not behave exactly like bash.

How the fortran program gets its input is up to you.

---

