---
title: "python output for shell command?"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by Unewbeginner on 2010-11-29
How could I make the output of a python program as a command? For example, my python program print: ```
cd /home/chris/Books/2010
``` and then Ubuntu shell execute the command above. Thanks!!

---

### Post by sisco311 on 2010-11-29
```
$(command)
```

See:
```
man bash | less +/"Command Substitution"
```

---

### Post by Unewbeginner on 2010-11-29
Sorry, when I add the code below in my python program, it doesn't work as I thought:

print "$ cd /home/chirs/book/2010"

anything I did wrong?

---

### Post by Unewbeginner on 2010-11-29
Sorry, when I add the code below in my python program, it doesn't work as I thought:

```
print "$ cd /home/chirs/book/2010"
```

anything I did wrong?

---

### Post by Unewbeginner on 2010-12-01
help please ......

---

### Post by sisco311 on 2010-12-01
Oh, you want something like:
```

import os

cmd='ls -al /home'
os.system(cmd)

```

[http://docs.python.org/tutorial/stdlib.html#operating-system-interface](http://docs.python.org/tutorial/stdlib.html#operating-system-interface)

---

### Post by AngusH on 2010-12-01
> **Unewbeginner said:**
> Sorry, when I add the code below in my python program, it doesn't work as I thought:
 
```
print "$ cd /home/chirs/book/2010"
```
 
anything I did wrong?
 
 Listen to sisco311, that's what you want, but also you don't want to be using that $ symbol. The shell shows it as an indicator of your privelidge level and the kind of input it wants, it's not a part of the command.
Angus

---

