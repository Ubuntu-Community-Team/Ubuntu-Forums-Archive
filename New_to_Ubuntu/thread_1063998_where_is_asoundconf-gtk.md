---
title: "where is asoundconf-gtk?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by skootar on 2009-02-08
My sound isn't working on 8.10.
I am trying to parse through the lines here:

[http://ubuntuforums.org/showthread.php?t=997506]("http://ubuntuforums.org/showthread.php?t=997506")

I assume I just keep crunching the lines in that post until it works?


THe very first instruction: asoundconf-gtk is a problem, it is not listed in synaptic, so I can't install it. THe apt-get command line for installing it also does not work.

---

### Post by ptn107 on 2009-02-08
Version 1.6-0ubuntu1 is in Synaptic in the multiverse repository.  Make sure multiverse is in your software sources by selecting System -> Administration -> Software Sources and selecting 'Software restricted by copyright or legal issues (multiverse)'.  Click close.

Then:
```
sudo apt-get install asoundconf-gtk
```
or install via synaptic.

---

