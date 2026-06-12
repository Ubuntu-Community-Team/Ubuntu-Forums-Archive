---
title: "how to get all the log message from the terminal"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by orky7 on 2011-04-19
in the terminal when ever we install a big software or something like that after some building/installing of the package the terminal window start truncating the log and only show some maximum lines, if i want the entire installation log which is truncated in the terminal in some file how should i do.

thanks

---

### Post by josephmills on 2011-04-19
I have wondering the same thing but have been using | grep as a filter but would love to know how to see more

---

### Post by DaithiF on 2011-04-19
Hi,
use tee to display output on screen and also write it to a file for later inspection.

```
your command 2>&1 | tee /path/to/logfile

```
2>&1 to redirect stderr output as well as stdout into tee.

---

### Post by josephmills on 2011-04-19
> **DaithiF said:**
> Hi,
use tee to display output on screen and also write it to a file for later inspection.

```
your command 2>&1 | tee /path/to/logfile

```
2>&1 to redirect stderr output as well as stdout into tee.

dear DaithiF.....
You :guitar:

---

