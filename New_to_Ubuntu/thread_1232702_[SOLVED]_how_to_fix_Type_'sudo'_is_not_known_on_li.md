---
title: "[SOLVED] how to fix Type 'sudo' is not known on line 54 in source list"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by joealanb on 2009-08-05
To the Geniuses in Ubuntu;

how do I fix this?  I keep getting the following error;

Type 'sudo' is not known on line 54 in source list /etc/apt/sources.list


Thanks,
joealanb

---

### Post by pedro3005 on 2009-08-05
What is the exact command you're trying to run? Because sudo must be before it all.

---

### Post by theozzlives on 2009-08-05
> **joealanb said:**
> To the Geniuses in Ubuntu;

how do I fix this?  I keep getting the following error;

Type 'sudo' is not known on line 54 in source list /etc/apt/sources.list


Thanks,
joealanb

Please post the contents of /etc/apt/sources.list

---

### Post by ptn107 on 2009-08-05
There is an error on line 54 of your sources.list file.  That file should not contain the word 'sudo'.  Press ALT+F2 and type:
```
gksu gedit /etc/apt/sources.list
```
in the box.  Find line 54 and fix it.

---

### Post by joealanb on 2009-08-05
ptn107  Perfect!  That fixed it!  I just deleted something I should not have pasted withought the command prompt!

---

### Post by joealanb on 2009-08-05
Solved

---

### Post by alphacrucis2 on 2009-08-05
> **ptn107 said:**
> There is an error on line 54 of your sources.list file.  That file should not contain the word 'sudo'.  Press ALT+F2 and type:
```
gksu gedit /etc/apt/sources.list
```
in the box.  Find line 54 and fix it.

Most likely the OP copied a PPA source line leaving off **deb** at the beginning or something like that.

---

### Post by NinjaNumberNine on 2009-08-05
> Please mark completed threads as [COLOR=Red]**[SOLVED]**[/COLOR], which lets us find solutions faster!

hi, ptn107. Saw your sig. How do you mark a thread as solved? (hehehe why should I ask, I never get any of mine solved)

---

### Post by doas777 on 2009-08-05
solved is broken for now (check the sticky in forum feedback for details)
for now, just add a solved tag to your query.

---

### Post by NinjaNumberNine on 2009-08-05
> solved is broken for now
oh, OK :D

---

### Post by jakebuntu on 2009-08-15
hello, i have had the same problem as the original poster, however when i press alt f2 and insert , it doesn't do anything.  GKSU tries to start i think but just closes again.
gksu gedit /etc/apt/sources.list

---

