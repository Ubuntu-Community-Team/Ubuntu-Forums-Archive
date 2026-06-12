---
title: "linux command not working"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by richa12 on 2011-07-21
egrep -w 'printf'|'scanf' /path/to/filename
command is not working.
It is showing some output random which then has to be exited

---

### Post by nomko on 2011-07-21
> **richa12 said:**
> egrep -w 'printf'|'scanf' /path/to/filename
command is not working.
It is showing some output random which then has to be exited
 
Can you post that output here? Without it is a bit difficult to tell you what the problem is and what the solution migth be.

---

### Post by richa12 on 2011-07-21
Hey!
that command worked actually i had to type it as
egrep -w 'printf|scanf' gr3.c

but now i want to know 1 more thing. i dont know why 
{
ps ux
ps -fu risharma
ps -fu
}
all these 3 commands are working but 
{
ps -fu unixstuff
ps risharma
}
these 2 commands are not worrking
my file system is like
/home/risharma/unixstuff

i am basically unclear as to what parameters etc does ps take?
pls help!

---

### Post by Vaphell on 2011-07-21
try ps with --help to get info about syntax and parameters
```
ps --help
```
-fu = full, user oriented

---

### Post by The Cog on 2011-07-21
For all the gory details, try the command
> man ps
and press Q (for Quit) when finished reading. **man** gives manual pages on pretty-much any command you can find. see "man man" for details.

---

