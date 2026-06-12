---
title: "BASH last run command in title"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by mjheagle8 on 2009-07-16
how do i put the command in my title? i'm playing around with $BASH_COMMAND but cant get it to work. here's the relevant section i have now in my bashrc:
```
PROMPT_COMMAND='echo -ne "\033]0;${USER}: ${PWD/$HOME/~}\007"'
```
thanks for any and all help.

---

