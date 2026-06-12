---
title: "how to clear list of recently entered console commands?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by genetik on 2009-09-20
When I open up a terminal and press "up arrow" it cycles through a list of recently entered commands.  I accidentally entered my root password and would like to clear this list.  How can I do it?

---

### Post by drs305 on 2009-09-20
Run this command:
```

history -c && source ~/.bashrc

```


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by MrWES on 2009-09-20
> **drs305 said:**
> Run this command:
```

history -c && source ~/.bashrc

```


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

You could add it to your .bash_alias file, so everytime it'll clear your history and then exit the shell.

```
alias out='history -c && exit'
```

So now when you want to exit a shell and clear the history, just type the word out.

Bill

---

