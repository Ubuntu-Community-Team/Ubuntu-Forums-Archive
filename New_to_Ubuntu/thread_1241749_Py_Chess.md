---
title: "Py Chess"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by cmcanulty on 2009-08-16
I installed PyChess twice but it never opens, any hints?

---

### Post by Soul-Sing on 2009-08-16
Are there errors when starting pychess via the therminal?
Did you enable via hardware drivers the drivers of your graphics card?

---

### Post by unutbu on 2009-08-16
There is a bug in python-opengl which might be affecting you. See
[http://ubuntuforums.org/showpost.php?p=7757477&postcount=5](http://ubuntuforums.org/showpost.php?p=7757477&postcount=5)
for a workaround.

---

### Post by Soul-Sing on 2009-08-16
There are other 3d chess clients by the way.

---

### Post by cmcanulty on 2009-08-16
This is what i get in terminal

cmcanulty@Ubuntu:~$ pychess
Exception in thread Thread-2:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/dist-packages/pychess/System/tsqlite.py", line 34, in run
    con = sqlite.connect(self.path)
OperationalError: unable to open database file

/usr/lib/python2.6/dist-packages/pychess/Players/engineNest.py:3: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import os, md5, imp

(pychess:4510): libglade-WARNING **: could not find glade file '/usr/lib/python2.6/glade/tipoftheday.glade'
Traceback (most recent call last):
  File "/usr/games/pychess", line 87, in <module>
    import pychess.Main
  File "/usr/lib/python2.6/dist-packages/pychess/Main.py", line 20, in <module>
    from pychess.widgets import tipOfTheDay
  File "/usr/lib/python2.6/dist-packages/pychess/widgets/tipOfTheDay.py", line 7, in <module>
    widgets = GladeWidgets("tipoftheday.glade")
  File "/usr/lib/python2.6/dist-packages/pychess/System/uistuff.py", line 198, in __init__
    self.widgets = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
RuntimeError: could not create GladeXML object
^C

---

### Post by unutbu on 2009-08-16
This doesn't look like the python-opengl error. 
Please hold off following the suggestion I gave in post #3, while we look at this a bit more...

Edit: 

How did you install pychess? 

Your version of pychess seems to be looking for 
/usr/lib/python2.6/glade/tipoftheday.glade

But according to 
[http://packages.ubuntu.com/search?searchon=contents&keywords=tipoftheday.glade&mode=&suite=jaunty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=tipoftheday.glade&mode=&suite=jaunty&arch=any)

pychess installs tipoftheday.glade in /usr/share/games/pychess/glade/tipoftheday.glade.

This seems to suggest you are not using the pychess package from the official Ubuntu repository.

---

### Post by cmcanulty on 2009-08-16
I just installed it from add remove applications. The GNU chess that comes with Ubuntu seems to have no features like playing level etc.

---

### Post by unutbu on 2009-08-16
cmcanulty, please open a terminal (Applications>Accessories>Terminal), type
```

apt-cache policy pychess

```
and post the output.

---

### Post by cmcanulty on 2009-08-17
cmcanulty@Ubuntu:~$ apt-cache policy pychess
pychess:
  Installed: (none)
  Candidate: 0.8.2-1
  Version table:
     0.8.2-1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
cmcanulty@Ubuntu:~$ 
cmcanulty@Ubuntu:~$

---

### Post by Soul-Sing on 2009-08-17
(pychess) python-pysqlite2 has to be installed.
You could remove pychess, and try to install it again, and take alook if it comes with (pychess) python-pysqlite2 while processing the installation.
Could also be a python-central problem...

---

### Post by unutbu on 2009-08-17
Edit: I did not see leoquant's message before posting this (below). Please try what he said first.
-----------------------------------------------------------
cmcanulty, please try the following

Click Applications>"Add/Remove" and remove the pychess package.
Then, in a terminal run:
```

which pychess                        # if pychess is still installed, this will show where it is located
dpkg --get-selections | grep chess   # list any packages with the word "chess" in its name

```
If you see any output, please post it.

If you do not see any output (meaning, hopefully, there is no more chess program installed on your system), then type

```

sudo apt-get install pychess         # install the pychess package
which pychess                        # show where your current pychess program is located
pychess                              # start pychess from the command line

```

If you run into any trouble, post the output.
If it works, you should also be able to run pychess by clicking Applications>Games>PyChess.

---

### Post by cmcanulty on 2009-08-17
OK I did a search for that in add/remove and it said no such file available

---

### Post by cmcanulty on 2009-08-17
Or sorry now I looked in Synaptic and several are listed, which one should I use, thanks

---

