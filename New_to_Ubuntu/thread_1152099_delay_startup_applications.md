---
title: "delay startup applications"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by mbzn on 2009-05-07
Stupid question, but what file do you set the time delay in startup applications? some of my apps give errors before my wireless connects so i want to delay them with about 5 seconds after startup.

Thanx in advance...

---

### Post by durand on 2009-05-07
If you add "sleep 5s;" to the start of the commands, that should do the trick.

---

### Post by mbzn on 2009-05-07
Thanx alot!!! where can i find all the commands that manipulates startup apps, i see things like <code> sh -c "sleep 5 </code>, and what is the s for in "5s". where can i learn about this?

---

### Post by durand on 2009-05-07
That command doesn't manipulate the startup applications. It's a general command for the linux shell which you can find in Applications > Accessories > Terminal. You might want to learn a few commands, it will improve your linux experience greatly!

Here are two good tutorials I found:

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

The s is for seconds. The ; is so that the sleep command runs and only when it finishes does the other command run.

---

### Post by durand on 2009-05-07
Oh and for the sleep help, you can type ***man** sleep* in the terminal. You can use *man command* for most programs and it will give you the program documentation.

---

### Post by mbzn on 2009-05-08
Thanx alot, i have began with some commands but was unaware of the sleep command as i am currently on beginner documentation...

Thanx again for your help...

---

### Post by billgoldberg on 2009-05-08
If you are serious about learning the cli and the in and outs of a Linux system, these lessons are a must:

[http://www.linux.org/lessons/](http://www.linux.org/lessons/)

---

