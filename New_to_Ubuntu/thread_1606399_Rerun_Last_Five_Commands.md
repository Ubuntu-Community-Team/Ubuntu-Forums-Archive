---
title: "Rerun Last Five Commands"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-10-26
Is it possible to rerun the last five commands in terminal. How about the last five commands before two commands ago?

---

### Post by cstudent on 2010-10-26
The up and down arrows will move you through the history of commands.

---

### Post by EnigmaticCoder on 2010-10-26
> **cstudent said:**
> The up and down arrows will move you through the history of commands.

Well what I meant was: Is there a single command to automatically run X number of commands from the history. So I could type

$ history
$ rerun [482, 487]

---

### Post by mikewhatever on 2010-10-26
histroty | tail -n X

where X is the number of commands.

---

### Post by KeLa on 2010-10-26
If you run command "history" and you got eg
....
399 ls
400 cd /
401 cat ./somethig
402 some command
403 some other command
404 history

then you can run those commands 399 to 403 by
!399 && !400 && !401 && !402 && !403

---

### Post by KeLa on 2010-10-26
> **mikewhatever said:**
> histroty | tail -n X

where X is the number of commands.

That gives you only the last x commands you have run.

---

### Post by Rinzwind on 2010-10-26
> **EnigmaticCoder said:**
> Well what I meant was: Is there a single command to automatically run X number of commands from the history. So I could type

$ history
$ rerun [482, 487]

Yes. Well I can tell you that...

tail -5 ~/.bash_history 

will give you the last 5 executed instructions as they where typed (so without any (line)numbers).
So all you need to do is pipe them and have them execute.

---

### Post by KeLa on 2010-10-26
> **Rinzwind said:**
> 

tail -5 ~/.bash_history 



That will not give you last 5 commands, it gives you last 5 commands that you run
before you started current terminal session.
So it's too old stuff.
Only way to get those last commands is to use "history" command.

---

### Post by EnigmaticCoder on 2010-10-26
> **KeLa said:**
> If you run command "history" and you got eg
....
399 ls
400 cd /
401 cat ./somethig
402 some command
403 some other command
404 history

then you can run those commands 399 to 403 by
!399 && !400 && !401 && !402 && !403

This solution works, although it'd be nice to input a range.

---

### Post by KeLa on 2010-10-26
I tried that with "for..loop" on command line but didn't get it work.

---

