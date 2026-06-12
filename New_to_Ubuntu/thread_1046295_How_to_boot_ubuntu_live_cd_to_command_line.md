---
title: "How to boot ubuntu live cd to command line?"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by adit on 2009-01-21
How to boot ubuntu 8.10 live cd to command line? What boot options should I give?

---

### Post by Sorivenul on 2009-01-21
Is there a particular reason you want to do this? 

There are a couple of ways to access a commandline session without going into the Desktop Environment.

1.) Hit "Escape" twice on the menu that allows you to "Try Ubuntu" or "Install Ubuntu". It should prompt you that you are leaving the graphical environment.

2.) Let it start up normally, and switch to a virtual terminal using "Ctrl+Alt+FN" where FN is one of your function keys (F1 - F8 should be active). "Ctrl+Alt+F7" should bring you back to graphical mode.

---

### Post by adit on 2009-01-21
Reason:
I got this message the first time I boot my ubuntu 8.10 live cd:
"The display server has been shut down 6 times in the last 90 seconds. It is likely that something bad is going on"
I actually don't want to install any desktop environment. I want to install only bash and gcc.

My computer is Dell Inspiron 1525.

---

### Post by Dr Small on 2009-01-21
> **adit said:**
> Reason:
I got this message the first time I boot my ubuntu 8.10 live cd:
"The display server has been shut down 6 times in the last 90 seconds. It is likely that something bad is going on"
I actually don't want to install any desktop environment. I want to install only bash and gcc.

My computer is Dell Inspiron 1525.
What about trying this?
[http://kmandla.wordpress.com/2007/11/29/miniubuntu-710-at-last-a-command-line-ubuntu-live-cd/](http://kmandla.wordpress.com/2007/11/29/miniubuntu-710-at-last-a-command-line-ubuntu-live-cd/)

---

### Post by Sorivenul on 2009-01-21
If you don't have any files that need backed up, it may be best to follow Dr Small's advice. Alternatively you could do a CLI (command line only) install from either the Alternate CD or the Minimial ISO for network installs. 

If you have files that need backed up, do that first. I would do this from the Ubuntu LiveCD if you can get it to work, otherwise you may be able to do some work from the recovery mode. Then reinstall.

---

