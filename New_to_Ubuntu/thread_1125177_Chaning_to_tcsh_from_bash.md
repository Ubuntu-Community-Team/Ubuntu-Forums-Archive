---
title: "Chaning to tcsh from bash"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by newcomer16 on 2009-04-14
hello guys.

I would like to install EGSnrc on ubuntu but am comfortable with tcsh instead of bash.
I would like to know how to change to tcsh as my default shell. Is it possible in ubuntu?

i only learnt that the deafult shell for ubuntu is bash when it failed to recognise the setenv command in emacs.

thanks.

---

### Post by rraj.be on 2009-04-14
Change the default shell in three steps:

   1. Launch Terminal
   2. From Edit-->Profile preferences
   3. In preferences, select “Title and command” and check 'Run a custome command insteed of my shell".
   4.type /bin/tcsh

That’s it. Now anytime you open a new terminal it will be the tcsh shell. To revert back to bash, follow the same procedure but replace /bin/tcsh with /bin/bash.

---

### Post by newcomer16 on 2009-04-14
thanx rajj.be.

I will try that n c.
good luck

---

