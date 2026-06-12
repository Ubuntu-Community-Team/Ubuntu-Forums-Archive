---
title: "Rhythmbox won't start"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by dondiego2 on 2010-02-02
[B]I may have posted this in the wrong place the first time and got no responses.  I though maybe I would have better luck here.

Rhythmbox won't start[/B] 			
 			 			 		   		 		 		Just in the last few days Rhythmbox and Listen Music Player will not open for some reason. This is what I get when I try to run them in terminal:

** (rhythmbox:6049): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:6049): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:6049): Rhythmbox-WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault

and this is what happens with Listen:

Traceback (most recent call last):
  File "listen", line 32, in <module>
    from option_parser import ListenOptionParser
  File "/usr/lib/listen/option_parser.py", line 25, in <module>
    from const import VERSION
  File "/usr/lib/listen/const.py", line 26, in <module>
    import gtk
ImportError: No module named gtk


Any help? The only thing that might be related is I installed Audacity recently but I don't remember if this happened at the same time.

---

### Post by jbcfarina on 2010-02-02
Seems to be a missing dependencie. Try to reinstall rhythmbox, it shows that it's dependant on python-gtk2 (on synaptic)

---

### Post by dondiego2 on 2010-02-02
> **jbcfarina said:**
> Seems to be a missing dependencie. Try to reinstall rhythmbox, it shows that it's dependant of python-gtk2 (on synaptic)


I have done that already.  I uninstalled it with the program manager and then reinstalled it and it still does the same thing.

---

### Post by Flimm on 2010-02-02
Open a terminal and tell us what these commands output:
```
python2.6 -c "import gtk"
python2.5 -c "import gtk"
ls -l /usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py
dpkg -s python-gtk2 | grep Status
dpkg -s python-gobject | grep Status
```

---

### Post by dondiego2 on 2010-02-02
> **Flimm said:**
> Open a terminal and tell us what these commands output:
```
python2.6 -c "import gtk"
python2.5 -c "import gtk"
ls -l /usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py
dpkg -s python-gtk2 | grep Status
dpkg -s python-gobject | grep Status
```


OK thanks.  I am at work now so this will have to wait until I get home this evening.  My work computer is totally Windows :(    I just get on the forum here :)

---

### Post by dondiego2 on 2010-02-02
> **Flimm said:**
> Open a terminal and tell us what these commands output:
```
python2.6 -c "import gtk"
python2.5 -c "import gtk"
ls -l /usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py
dpkg -s python-gtk2 | grep Status
dpkg -s python-gobject | grep Status
```

Here are my results from these commands:

carl@carl-desktop:~$ python2.6 -c "import gtk"
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ImportError: No module named gtk
carl@carl-desktop:~$ python2.5 -c "import gtk"
No command 'python2.5' found, did you mean:
 Command 'ipython2.5' from package 'ipython' (universe)
python2.5: command not found
carl@carl-desktop:~$ ls -l /usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py
lrwxrwxrwx 1 root root 43 2010-01-17 11:45 /usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py -> /usr/share/pyshared/gtk-2.0/gtk/__init__.py
carl@carl-desktop:~$ dpkg -s python-gtk2 | grep Status
Status: install ok installed
carl@carl-desktop:~$ dpkg -s python-gobject | grep Status
Status: install ok installed
carl@carl-desktop:~$

---

### Post by Flimm on 2010-02-03
Wow, something's wrong with your Python installation. Which version of Ubuntu are you running?

I still need more info to pinpoint the problem, can you run these commands please and post the ouput:
```
python2.6 -c "import sys; print sys.path"
cat /etc/python2.6/sitecustomize.py
cat /usr/lib/python2.6/sitecustomize.py
cat ~/.profile | grep -i PYTHON -C 5
cat ~/.bashrc | grep -i PYTHON -C 5
```

You might want to try reinstalling Python's GTK bindings, like this:```
sudo apt-get install --reinstall python-gtk2 python-gobject
```

---

### Post by dondiego2 on 2010-02-03
> **Flimm said:**
> Wow, something's wrong with your Python installation. Which version of Ubuntu are you running?

I still need more info to pinpoint the problem, can you run these commands please and post the ouput:
```
python2.6 -c "import sys; print sys.path"
cat /etc/python2.6/sitecustomize.py
cat /usr/lib/python2.6/sitecustomize.py
cat ~/.profile | grep -i PYTHON -C 5
cat ~/.bashrc | grep -i PYTHON -C 5
```You might want to try reinstalling Python's GTK bindings, like this:```
sudo apt-get install --reinstall python-gtk2 python-gobject
```


I tried reinstalling and it did but it did not fix the problem.  I still get the same error when I try to run it in the terminal.  Here is the output from running the commands above: (I am running 9.10)
carl@carl-desktop:~$ python2.6 -c "import sys; print sys.path"
['', '/usr/local/lib/python26.zip', '/usr/local/lib/python2.6', '/usr/local/lib/python2.6/plat-linux2', '/usr/local/lib/python2.6/lib-tk', '/usr/local/lib/python2.6/lib-old', '/usr/local/lib/python2.6/lib-dynload', '/usr/local/lib/python2.6/site-packages']
carl@carl-desktop:~$ cat /etc/python2.6/sitecustomize.py
# install the apport exception handler if available
try:
    import apport_python_hook
except ImportError:
    pass
else:
    apport_python_hook.install()
carl@carl-desktop:~$ cat /usr/lib/python2.6/sitecustomize.py
# install the apport exception handler if available
try:
    import apport_python_hook
except ImportError:
    pass
else:
    apport_python_hook.install()
carl@carl-desktop:~$ cat ~/.profile | grep -i PYTHON -C 5
carl@carl-desktop:~$ cat ~/.bashrc | grep -i PYTHON -C 5

---

### Post by dondiego2 on 2010-02-03
OK - I feel like a dummy.  I heard someone talking about Python on a podcast last week and I thought it sounded cool and I wanted to learn it.  So not realizing I already had it I Googled it and downloaded it and installed it from the website.  I think that is when all my problems started.  Again, like an idiot I went to the package manager (ubuntu software center) and tried to uninstall Python 2.6 so I could do a fresh reinstall.  Doing that crashed my computer and I lost my desktop.  The only think I had was a full screen terminal and I couldn't figure out how to recover.

So here I am after reinstalling from my installation disk - starting all over again.  Oh well, this is the second time I have screwed something up and had to do this.  I guess it's a good way for a new guy to learn.... Going on 2 months with Ubuntu and I sure am learning a lot!

Thanks for your help.

---

### Post by kevincmaker on 2012-12-05
> **Flimm said:**
> Wow, something's wrong with your Python installation. 

...
...

You might want to try reinstalling Python's GTK bindings, like this:```
sudo apt-get install --reinstall python-gtk2 python-gobject
```

Thanks Flimm! Solved my problem :)

---

