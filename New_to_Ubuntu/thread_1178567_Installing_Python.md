---
title: "Installing Python"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by k_squired on 2009-06-04
I tried to execute these commands
apt-get install python2.4 python-gtk2 python-glade2
(and an abbreviated version with just the python) from this thread: [http://ubuntuforums.org/showthread.php?t=416660 ]("http://ubuntuforums.org/showthread.php?t=416660")but alas, it says it can't do it access is denied.  It is in my var folder, but the root owns it.  I was having the same issue as the original threadmaker.  Becuase root owns it, I cannot change permissions.  How do I get around this?

---

### Post by Tibuda on 2009-06-04
You should use apt-get with sudo:
```
sudo apt-get install python2.4 python-gtk2 python-glade2
```

Read more about installing Ubuntu software in: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Celauran on 2009-06-04
Python is installed by default and 2.4 is an old version -- the post you linked was from 2007.

As for the access denied bit, you need to prefix apt-get with sudo.

```
sudo apt-get install whatever
```

---

### Post by k_squired on 2009-06-04
Um.. I tried to install packages [http://packages.ubuntu.com/jaunty/](http://packages.ubuntu.com/jaunty/) for all the dependencies it stated in the chess program itself.  Then it just started to quit when I clicked on 3d.  ( Is there a standard error log somewhere?)

Then, I installed the defualt packaged using the sudo command - I did update my ubuntu, I dunno if a newer version of python came with that or not (can I check?) still, now the entire chess program just quits.  

Oh, and thanks for the help.

---

### Post by Celauran on 2009-06-04
```
python -V
```

will show you the installed version.

---

### Post by k_squired on 2009-06-04
Python 2.6.2

Is there an error log somewhere?  You know, the equivalent of windows message-boxes when windows programs fail?

Also, could my dependency packages be for an obsolete version?  Those versions do not seem to correspond to Python.

---

### Post by Celauran on 2009-06-04
> **k_squired said:**
> 
Is there an error log somewhere?
Error logs are typically stored in /var/log

---

### Post by k_squired on 2009-06-04
Uhh... Where, exactly, are the error logs?

---

### Post by Temposs on 2009-06-04
The way you want to check errors on this program is to open a terminal and run the program from terminal. It should then output any errors as they happen.

---

### Post by k_squired on 2009-06-05
On the terminal log, this was the story:

eException.message has been deprecated as of Python 2.6
  print 'Failed to load GGZ config: %s' % e.message
Failed to load GGZ config: 
Using OpenGL:

VENDOR=Mesa Project
RENDERER=Software Rasterizer
VERSION=2.1 Mesa 7.4
EXTENSIONS=GL_ARB_depth_texture ...[ huge list ensues]

Traceback (most recent call last):
  File "/var/lib/python-support/python2.6/glchess/gtkui/chessview.py", line 168, in __expose
    self.view.feedback.renderGL()
  File "/var/lib/

[similiar huge list ensues]

 File "/usr/lib/python2.6/dist-packages/OpenGL/arrays/nones.py", line 32, in zeros
    raise TypeError( """Can't create NULL pointer filled with values""" )
TypeError: ("Can't create NULL pointer filled with values", 'Failure in cConverter <OpenGL.converters.SizedOutput object at 0x93a1c6c>', [GL_TEXTURE_2D], 1, <OpenGL.wrapper.glGetIntegerv object at 0x93b0aac>)

sh: bug-buddy: not found


uh... what does all this mean?

---

