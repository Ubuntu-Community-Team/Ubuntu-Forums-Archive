---
title: "Variable initialization"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by newport_j on 2010-02-07
I have a C program that has many sub programs. I want to know how many times a certain subprogram executes. I put a line in that subprogram that says 

repcount = repcount + 1;

where repcount is my counter and I add 1 to it each time the execution enters that subprogram. I initialized repcount in the main program; obviously I do not want to initialize repcount in the subprogram because that would mean that repcount is set back to zero each time I enter the subprogram. 

However, the compiler does not like it saying that repcount has not been initialized - in the subprogram. Well, repcount is a global variable and I initialized in the main program only once. 

How do I remedy this situation since, repcount cannot be initialized in the the subprogram of interest even though the complier complains if I do not initialize it there?

newport_j

---

### Post by coldfusion1313 on 2010-02-07
Wrong thread try:
[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)
That is where programming and developing are talked about.

---

