---
title: "Inittab Virtualconsoles tty's"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by ronaldprettyman on 2009-07-01
OK I love ubuntu its great, but where do I specify virtualterminal/virtualconsoles, tty's
alt+f/[1-6]/
like in /etc/inittab ?

Not trying to specify runlevel

And whats up with the run levels? 2-5 all have multiuser and X

---

### Post by bodhi.zazen on 2009-07-01
Runlevels 2-5 have been that way (multiuser and X) for as long as I can remember.

What is you want to do with your tty ? and what version of Ubuntu ?

Try looking in edit the /etc/default/console-setup and reading about upstart.

[http://www.linux.com/feature/125977?theme=print](http://www.linux.com/feature/125977?theme=print)

---

### Post by ronaldprettyman on 2009-07-01
> **bodhi.zazen said:**
> 
Try looking in edit the /etc/default/console-setup and reading about upstart.
[http://www.linux.com/feature/125977?theme=print](http://www.linux.com/feature/125977?theme=print)
Thanks
> **bodhi.zazen said:**
> 
Runlevels 2-5 have been that way (multiuser and X) for as long as I can remember.

In ubuntu you mean? I was just wondering why their no multiuser no gui, limited networking, etc... But reading though the upstart thing, it makes since. 
Thanks

---

### Post by bodhi.zazen on 2009-07-01
> **ronaldprettyman said:**
> Thanks

In ubuntu you mean? I was just wondering why their no multiuser no gui, limited networking, etc... But reading though the upstart thing, it makes since. 
Thanks

You are most welcome. 

Of course in Ubuntu, :lolflag:

If you are new to Linux, and do not know what a run level is, or that you need to run "startx" or "startkde" it is usually anticlimactic to install Slackware.

---

### Post by ronaldprettyman on 2009-07-01
startx eh, just going all out old school on me.


The answer to the question was for people landing on this page from google or whatever
```
/etc/event.d/tty/[1-6]/
```

---

