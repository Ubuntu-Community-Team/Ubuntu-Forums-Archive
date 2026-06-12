---
title: "Can't install software from Software Center"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by JaxM on 2010-05-28
Just recently I've been trying to install a few apps from the Software Center but I've only been getting a prompt saying: "**Previous installation hasn't been completed**

 The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software."

I don't have anything being installed or uninstalled. My internet connection (wireless) is fine. So, I don't understand what's wrong. It says Previous Installation but I don't remember what I was trying to install. I'm running Ubuntu 10.04 on a dv7-1464nr HP Netbook if that helps. Any help from others is greatly appreciated.

---

### Post by hansdown on 2010-05-28
Hi JaxM.

You may have broken packages.

The easy way to check, is click system> administration> synaptic package manager.

After entering your password, click custom filters in the bottom left.

Next, click broken in the top left.

If any are broken, you will see them, and be given an option to fix them.

---

### Post by ranch hand on 2010-05-28
Well something seems to be bothering dpkg which is the base of all your package management.

I would, first, run, in terminal;
```

sudo dpkg --configure -a

```
That should clear the problem, if there is one, or at least give you some error messages.

If you get an error message post it here.

If all you get is another prompt, go to synaptic and try installing there (or better use apt-get install).

If you get errors post them here.

I do not think this has to do with your hardware but a model number is not real good information.  Most people on here are not going to look that up to see what you have.  Some real info would be a good thing to give.   You can see my sig for an example of what is needed along those lines.

Like I say though, I think this really is a dpkg problem or maybe just the USC.  Let us find out.

---

### Post by JaxM on 2010-05-28
> **ranch hand said:**
> Well something seems to be bothering dpkg which is the base of all your package management.

I would, first, run, in terminal;
```

sudo dpkg --configure -a

```
That should clear the problem, if there is one, or at least give you some error messages.

If you get an error message post it here.

If all you get is another prompt, go to synaptic and try installing there (or better use apt-get install).

If you get errors post them here.

I do not think this has to do with your hardware but a model number is not real good information.  Most people on here are not going to look that up to see what you have.  Some real info would be a good thing to give.   You can see my sig for an example of what is needed along those lines.

Like I say though, I think this really is a dpkg problem or maybe just the USC.  Let us find out.

Thanks so much it worked :D Nothing like a clogged drain :P (hope you get the analogy xD )

And thanks for the specs tip.

---

### Post by ranch hand on 2010-05-28
I will have you know that  I am very good at getting things in that condition (including drains).  This comes in handy if you want to learn how the plumbing of package management works.

There are a number of commands for dpkg and I recommend a look at the man page.  It may come in handy some time to just have looked it over (might ring a bell  when something comes up).  Very powerful.

One thing that I did discover is that the commands seem to take a more aggressive approach when used in the "rescue a screwed OS" (or whatever the real name is) mode on the Live DVD.  If some thing is broken, and you know the command for dpkg, it is real fun to watch the OS suddenly come back to life.

Have FUN.

---

### Post by ranch hand on 2010-05-28
You ought to mark this thread solved.  At the top of the page there is "Thread Tools" you can mark it there.

This will save folks from trying help.  It will also indicate a possible solution to someone doing a forum search with a similar problem.

---

### Post by kcaulley on 2010-08-20
Hi!
I found this post that I thought would fix my problem but when I opened Syanaptic Package Manger I received the error
E; dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E;_cache->open() failed, please report.
When I run the above command I get:
Setting up firefox (3.6.9~hg20100817+nobinonly-0ubuntu1~umd2~lucid)....
in the terminal box and it must hang up. I have left it for over 30 min's and nothing happens. Could you please help? Yes I'm new to Linux. It seems the more I try to leave Micro$oft the less I can do.

Thanks in advance.
Kurt

---

### Post by dil1857 on 2010-09-08
> **kcaulley said:**
> Hi!
I found this post that I thought would fix my problem but when I opened Syanaptic Package Manger I received the error
E; dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E;_cache->open() failed, please report.
When I run the above command I get:
Setting up firefox (3.6.9~hg20100817+nobinonly-0ubuntu1~umd2~lucid)....
in the terminal box and it must hang up. I have left it for over 30 min's and nothing happens. Could you please help? Yes I'm new to Linux. It seems the more I try to leave Micro$oft the less I can do.

Thanks in advance.
Kurt

same probalm

---

