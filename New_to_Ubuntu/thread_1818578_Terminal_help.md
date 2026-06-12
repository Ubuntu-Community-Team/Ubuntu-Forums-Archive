---
title: "Terminal help"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by meselsohn on 2011-08-05
Hi,

I'm on the latest ubuntu system, and I recently removed a program manually by deleting its folder and directories. When I open a new terminal now, it says 

"bash: /home/file-name.setup No such file or directory"

before the starting command line. It's not a big problem, but I'd like to get rid of this echo. I've tried opening /bin/bash in my text editors, but none seem to give any coherent thing to look at.

Help appreciated please.  :-)

---

### Post by mimiteto on 2011-08-05
Hello :) Try opening ~/.bashrc and look there :)
Btw, what was the program that U ripped of ?

---

### Post by fdrake on 2011-08-05
> **meselsohn said:**
> Hi,

I'm on the latest ubuntu system, and I recently removed a program manually by deleting its folder and directories. When I open a new terminal now, it says 

"bash: /home/file-name.setup No such file or directory"

before the starting command line. It's not a big problem, but I'd like to get rid of this echo. I've tried opening /bin/bash in my text editors, but none seem to give any coherent thing to look at.

Help appreciated please.  :-)

what's 'file-name.setup'  ?

---

### Post by meselsohn on 2011-08-05
Ah perfect, I edited the ~/.bashrc file and got rid of the old source commands. Thanks much for your help  (:

The thing I deleted was called ccp4, it's a suite of programs for processing x-ray diffraction data.

---

### Post by fdrake on 2011-08-05
> **meselsohn said:**
>  called ccp4, it's a suite of programs for processing x-ray diffraction data.
cool i did not know about a program like that.. :P:P

---

### Post by elliotn on 2011-08-05
didn't know either

---

