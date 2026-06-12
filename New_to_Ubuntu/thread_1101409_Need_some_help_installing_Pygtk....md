---
title: "Need some help installing Pygtk..."
date: 2009-03-20
forum: New to Ubuntu
---

### Post by food789 on 2009-03-20
I'm trying to install pygtk (mainly for "learning" puposes ;)) and I get an error.

In the README file it tells me to type:
```
$ ./configure --prefix=<prefix where python is installed>
$ make
$ make install
```

So I find where python is located then I type: ./configure --prefix=/usr/bin/python
The configure runs, but then an error pops up saying:
```
checking for GLIB - version >= 2.8.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: gobject is required to build pygtk?

```

Is there a way to fix this error so I can install pygtk?

UPDATE:
As you can see, one line of the error says "configure: error: gobject is required to build pygtk?".
This is where another problem comes in. I looked in Synaptic Package Manager and it shows I already have python-gobject... Also, when I try to install gtk-recordmydesktop it tells me I need pygtk >= 2.4, however I have downloaded pygtk 2.12...

Help would be appreciated...

---

### Post by taurus on 2009-03-20
You probably need to install the libglib2.0-dev package first.  It should be in the repos.

---

### Post by food789 on 2009-03-20
Hmm... Seems like I'm in Package hell right now...

I need libglib2.0-dev to install pygtk-2.12.0.
I need libglib2.0-0 to install libglib2.0-dev.
I need libpcre3 to install libglib2.0-0.
And I can't install libpcre3 because a later version is already installed...

---

### Post by food789 on 2009-03-20
Hmmm... If no one can help me with that, can someone recommend me a good screen recorder? I've been trying to get recordmydesktop to work but as you can see it isn't working...

---

### Post by taurus on 2009-03-20
You know pygtk is in the repos, right?

---

### Post by lykwydchykyn on 2009-03-20
You can just install python-gtk2 from the repositories if you want pygtk.  It's at version 2.13.0.  Is there a reason you need an older version?

---

### Post by food789 on 2009-03-20
> **taurus said:**
> You know pygtk is in the repos, right?

Yeah, I know. But the problem is that I can't compile the gtk-recordmydesktop code. I use ./configure and an error shows saying I need pygtk >=2.4 yet the most recent version of pygtk seems to be 2.13.
I just need to install gtk-recordmydesktop...

---

### Post by taurus on 2009-03-20
Try this version, [http://www.getdeb.net/app/RecordMyDesktop](http://www.getdeb.net/app/RecordMyDesktop).

---

### Post by food789 on 2009-03-20
> **taurus said:**
> Try this version, [http://www.getdeb.net/app/RecordMyDesktop](http://www.getdeb.net/app/RecordMyDesktop).

That worked! Thanks for the help.

---

