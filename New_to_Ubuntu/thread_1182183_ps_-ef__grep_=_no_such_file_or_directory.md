---
title: "ps -ef | grep = no such file or directory?"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by Mr_H on 2009-06-08
I upgraded to Jaunty yesterday on my home machine.  Ever since then, I get an error when I use my oft used command: **ps -ef|grep <whatever>**.  The output looks like this:

```
ps -ef | grep apache
ls: cannot access apache: No such file or directory

```

I've done this command a lot in the past on this machine without any problems, and it works on my server (Ubuntu Server OS).  I've looked around and I'm having a devil of a time finding any suggestions as to why this is happening.

Any thoughts?
Thanks

---

### Post by LMZKJ on 2009-06-08
What happens if you just run "ps -ef"?  Do you get a list of results there?

---

### Post by Mr_H on 2009-06-08
ps -ef gives me the regular listing as you'd expect.  ps -ef|more does the page spacing as well.

---

### Post by bodhi.zazen on 2009-06-08
Where did the "ls" come from ?

> root# ps -ef | grep bash
root      3693  3692  0 21:26 pts/0    00:00:00 -bash
root      3711  3693  0 21:45 pts/0    00:00:00 grep bash

---

### Post by Mr_H on 2009-06-08
Good eye! I hadn't thought about that, I Thought the problem lay with grep.

For some reason, the following line was in .bashrc

```
alias grep='ls --color=auto'
```

I have no idea why that was there, but I removed the ls and changed it to grep and viola, it works again.  I wonder if the upgrade just automated a change there or something.

Thanks for the help...simple solution, I guess I've just been staring at it too much for it all to click.

---

