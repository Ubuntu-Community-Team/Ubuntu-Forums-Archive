---
title: "What prompt did I change change to."
date: 2011-06-21
forum: New to Ubuntu
---

### Post by cowboy.bebop on 2011-06-21
I was playing with commands and I did PS1='\!$' and it came up with 794$ what is this? I saw the number, I assumed it was the id of a user on the system.

---

### Post by gmargo on 2011-06-21
See the **bash(1)** man page, under "PROMPTING".  

The "\!" in your prompt expands to "the history number of this command".  Enter the command "history" to see the whole command history list.

---

### Post by cowboy.bebop on 2011-06-21
\!
the history number of this command

\$
if the effective UID is 0, a #, otherwise a $

But whats the purpose of the history number, the uid I can understand but why the history of a prompt, maybe I am just not understanding it correctly.

And rather the commands used as \! \$ they can connected as one whole statement? eg PS1='\!$' ?

---

