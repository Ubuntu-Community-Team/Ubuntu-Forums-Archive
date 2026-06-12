---
title: "Does Periodic Maintenance Exist For Xubuntu [Linux] users ?"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by faron45 on 2009-04-01
Hellllppppppppp ! Okay,so it may not be quite that serious.What I need to know,is if there is some sort of periodic maintenance that I must do now that I run a Linux [xubuntu] operating system.
 
 I knew with "windows",every once in awhile,I would have to do things like empty temporary internet files,delete cookies,clear cache,etc.And,like once a year or so,I would even go so far as to just re install the whole os from scratch.So,now that I'm not running a "windows" o.s. anymore,is there any of that type of stuff that I still have to do once in awhile ?
 
 I've been running xubuntu for almost a year now & I'm just a little worried that things may be getting a little clogged up somewhere or another.So,what do you guys/gals think ?

---

### Post by egalvan on 2009-04-01
> **faron45 said:**
> some sort of periodic maintenance that I must do now that I run a Linux [xubuntu] os.
 
 with "windows",every once in awhile,I would empty temp internet files,delete cookies,clear cache,etc. like once a year or so,I would just re install the whole os .,is there any of that type of stuff that I still have to do once in awhile ?
 
 I've been running xubuntu for almost a year now & I'm worried that things may be getting  clogged up .So,what do you guys/gals think ?

I've got Firefox set to clean "cookies" and "cache" on exit...

I have Synaptic set to erase un-needed files (old/out-dated downloads)...

I run the following on occasion...

```
sudo apt-get autoremove

sudo apt-get autoclean

sudo apt-get clean
```


There are threads on "taking out the trash" (emptying the "trash folder")


But all-in-all, *nix is much tidier than Windows ever was, or will be...

ErnestG

---

### Post by faron45 on 2009-04-01
Thanks very much ErnstG.Much appreciated.Now,does anybody know of any links off hand that I could browse to learn about such things ? I suppose I could just Google it,huh ?

---

### Post by |Mitch| on 2009-04-01
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

There's a thread you might be interested in

---

### Post by egalvan on 2009-04-01
> **faron45 said:**
> Thanks very much ErnstG.Much appreciated.Now,does anybody know of any links off hand that I could browse to learn about such things ? I suppose I could just Google it,huh ?

For Firefox, go to 

menu -> edit -> preferences -> privacy

and set them to your liking.


For Synaptic, got to

settings -> preferences -> files

and set them to your liking.


For the codes I gave, create an empty document file in your
 ~/bin directory, 
call it something like clean.sh
and paste the following into it:

```
#!/bin/bash
### commands to clean drive of excess garbage
### from ubuntu forums
### http://ubuntuforums.org/showthread.php?t=1113381
### 01-april-09

sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
sudo dpkg --configure -a
```

By the way, the lines with **three** # are notes to me, to remind me of what the script does, and where I got it from...
the first line with only **one** # is needed to make the file a script.

Now go and use the "search" function on this forum to find info on "cleaning trash folders" :)
(what fun is having ALL your work done for you?)

ErnestG

---

### Post by DarkReaper79 on 2009-04-01
would using it, breaking it, then fresh install be periodic maintenance:lolflag::guitar:

---

### Post by linuxuser21 on 2009-04-01
> **egalvan said:**
> I've got Firefox set to clean "cookies" and "cache" on exit...

I have Synaptic set to erase un-needed files (old/out-dated downloads)...

I run the following on occasion...

```
sudo apt-get autoremove

sudo apt-get autoclean

sudo apt-get clean
```


There are threads on "taking out the trash" (emptying the "trash folder")


But all-in-all, *nix is much tidier than Windows ever was, or will be...

ErnestG

Thanks for this.  I already knew there was an autoremove; but, I didn't know about the rest of them.  I feel cleaner now.  lol.

---

### Post by egalvan on 2009-04-01
> **DarkReaper79 said:**
> would using it, breaking it, then fresh install be periodic maintenance:lolflag::guitar:

Actually the best kind there is!

:popcorn:

---

### Post by egalvan on 2009-04-01
> **linuxuser21 said:**
> Thanks for this.  I already knew there was an autoremove; but, I didn't know about the rest of them.  I feel cleaner now.  lol.

Try 

```
man apt-get
```

lots more there... :)

---

### Post by hyper_ch on 2009-04-02
> **egalvan said:**
> I run the following on occasion...

```
sudo apt-get autoremove

sudo apt-get autoclean

sudo apt-get clean
```

and why do you run those?

---

### Post by egalvan on 2009-04-02
> **hyper_ch said:**
> and why do you run those?

sorry for the delay in responding...


Quote from the **man **page for apt-get

[B] *clean*
           clean [COLOR="Red"]clears out the local repository of retrieved package files.[/COLOR]
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(8) method, clean is run automatically.
           [COLOR="Red"]Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.
[/COLOR]
      * autoclean*
           Like clean, autoclean [COLOR="Red"]clears out the local repository of retrieved
           package files[/COLOR]. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

      * autoremove*
           autoremove is used to [COLOR="Red"]remove packages that were automatically
           installed[/COLOR] to satisfy dependencies for some package [COLOR="Red"]and that are no
           more needed.[/COLOR]
[/B]


Yes, a bit redundant, but it removes un-wanted stuff from my hard drive.

clean & autoclean are not both needed...
but I'm lazy and haven't cleaned up that "clean-drive" script yet...

---

