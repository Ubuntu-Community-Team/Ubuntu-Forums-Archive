---
title: "Dpkg probrem?"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by nene7 on 2010-01-31
hi, 
 my girlfriend computer it say anytime that i tried to install or upgrade:
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.I tried to wrote in the terminal :
> sudo dpkg 
uto upgrade but it say the same it has to be manually. What i have to do?
i wrote in terminal > sudo dpkg --configure -abut it appear this:

---

### Post by candtalan on 2010-01-31
it asks you to type in terminal

sudo dpkg --configure -a

it will then ask for the user password (of your girlfriend?)

hope that helps

---

### Post by nene7 on 2010-01-31
nop, 
it say sometime about bus problem.

---

### Post by candtalan on 2010-02-01
I do not know, sorry.

---

### Post by pcolamar on 2010-02-01
I have just the same problem (jaunty 9.04).
I am wondering if it didn't come from a recent update !
Unfortunately i cannot go to Synaptic to roll back... it just doe not start.

Please help.
-R.

---

### Post by pcolamar on 2010-02-01
I found somehow a solution.
I knew I had a broken install of a kernel so I run:

sudo find / -name '*2.6.31-16''

Just to see what file would it find. Once I saw they were all belonging to the broken install I run again:

sudo find / -name '*2.6.31-16' -exec rm -rf {} \;

**_BE CAREFUL_**, this last command deletes anything the "find" command had found without asking confirmation.

After that  " sudo dpkg --configure -a " worked fine.

Regards

Palmer

---

