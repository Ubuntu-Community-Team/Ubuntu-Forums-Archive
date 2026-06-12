---
title: "apt-get purge"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by ubudog on 2009-08-04
What does apt-get purge do?  I know apt-get remove, removes an application, but what does apt-get purge do?   Thanks :)

---

### Post by pedro3005 on 2009-08-04
Completely removes an application. Not sure of the difference between purge and remove, maybe someone can enlighten us.

---

### Post by ubudog on 2009-08-04
I believe it removes the files too.  I removed a game via apt-get remove but the config files and all the game files were still there.  I believe apt-get purge removes all those files.  Someone correct me if I'm wrong. ;)

---

### Post by philcamlin on 2009-08-04
> **ubudog said:**
> I believe it removes the files too.  I removed a game via apt-get remove but the config files and all the game files were still there.  I believe apt-get purge removes all those files.  Someone correct me if I'm wrong. ;)

yes your right purge removes the config files and the whole application etc while remove just remove the application :popcorn:

---

### Post by ubudog on 2009-08-04
> **philcamlin said:**
> yes your right purge removes the config files and the whole application etc while remove just remove the application :popcorn:

Ok.  Thanks for the help!  That solves my question :D

---

### Post by Wataru8675 on 2009-08-05
> **philcamlin said:**
> yes your right purge removes the config files and the whole application etc while remove just remove the application :popcorn:
So if you were to use apt-get purge on a program like Wine...would it remove Wine and everything that runs on Wine (i.e. webcam software, several games, Quicktime, etc.)?

---

### Post by philcamlin on 2009-08-05
> So if you were to use apt-get purge on a program like Wine...would it remove Wine and everything that runs on Wine (i.e. webcam software, several games, Quicktime, etc.)?i believe so :popcorn:

---

### Post by ubudog on 2009-08-05
> **philcamlin said:**
> i believe so :popcorn:

Thanks everyone! :D

---

### Post by credobyte on 2009-08-05
> **Wataru8675 said:**
> So if you were to use apt-get purge on a program like Wine...would it remove Wine and everything that runs on Wine (i.e. webcam software, several games, Quicktime, etc.)?

Personally, purge didn't worked for Wine ( a few [COLOR=DimGray]custom locations[/COLOR] of wine files can be found at [http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html](http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html) ).

---

### Post by bodhi.zazen on 2009-08-05
From : [http://manpages.ubuntu.com/manpages/jaunty/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/apt-get.8.html)

> 
        purge
            purge is identical to remove except that packages are removed and
            purged (any configuration files are deleted too). 

In English this means the config files in /etc are removed, but the config files in $HOME are not. So in the case of wine , ~/.wine would not be removed by apt-get --purge .

In practice not everything is completely purged with the purge option. The data in a data base (postgresql / mysql) is not removed for example.

---

### Post by ubudog on 2009-08-05
> **bodhi.zazen said:**
> From : [http://manpages.ubuntu.com/manpages/jaunty/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/apt-get.8.html)

 

In English this means the config files in /etc are removed, but the config files in $HOME are not. So in the case of wine , ~/.wine would not be removed by apt-get --purge .

In practice not everything is completely purged with the purge option. The data in a data base (postgresql / mysql) is not removed for example.

Thank you Bodhi,  that explains everything to me.  Thanks so much everyone! :)

---

