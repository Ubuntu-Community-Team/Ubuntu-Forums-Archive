---
title: "terminal"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by colormoon on 2009-02-02
Hello,
I've any question about terminal. When I open terminal, it'll show 
user@server$
the question is: can I change 'server' name?
thanks

---

### Post by jerome1232 on 2009-02-02
Yes what it's showing is your host name to change it

```
sudo hostname *newhostname*
sudo nano /etc/hostname  # put the new hostname in here
sudo nano /etc/hosts  # edit the entry that says 127.0.1.1 and replace your old hostname with the new hostname
```

That should do it right there.

---

### Post by colormoon on 2009-02-02
thank you for your reply
but when I follow your step....
my xubuntu cannot do anything else, except thunar and firefox.
what should I do??:(

---

### Post by kerry_s on 2009-02-02
> **colormoon said:**
> Hello,
I've any question about terminal. When I open terminal, it'll show 
user@server$
the question is: can I change 'server' name?
thanks

change it in your ~/.bashrc, read this:
[http://www.ibm.com/developerworks/linux/library/l-tip-prompt/](http://www.ibm.com/developerworks/linux/library/l-tip-prompt/)

---

