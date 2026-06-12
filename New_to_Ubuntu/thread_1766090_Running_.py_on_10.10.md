---
title: "Running .py on 10.10"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by maaarg on 2011-05-23
Hi all,

Summer goal is to learn Python, but I'm having some issues even getting started. I'm using Google's Python class, found here:
[http://code.google.com/edu/languages/google-python-class/set-up.html]("http://code.google.com/edu/languages/google-python-class/set-up.html")

I downloaded the zipped exercise file and unzipped it to ~/python and then attempted to run the test program, hello.py, that was included there. So here's what I did and the response I got

~/python/google-python-exercises$ python hello.py
python2.5: command not found

typing 'python' in command line to try to get a read on the version also resulted in 'command not found.' The file, hello.py, can be opened and edited in emacs, so I'm positive it exists, and  in that directory.

Since then I've attempted (perhaps unwisely) to install Python 2.7 using apt-get, but the results remained the same.

---

### Post by Toz on 2011-05-23
Perhaps your python symbolic link is broken. Can you reply back with the results of the following commands:
```
which python
```

If you get /usr/bin/python:```
file /usr/bin/python
```

and```
ls -l /usr/bin/python*
```

As a temporary workaround, and if you've installed 2.7, try running the command like this```
python2.7 hello.py
```

---

### Post by maaarg on 2011-05-23
Thanks--the workaround you suggested worked perfectly-- I suppose I can just use chmod to avoid having to type python2.7 every time, but should there be an easier way to do that?

As for your first suggestions:

got /usr/bin/python for the first command,

/usr/bin/python: symbolic link to `python2.6'  for the second

and the third showed python2.6 and python2.7 in the directory (I can give the actual response if that would be helpful).

---

### Post by Toz on 2011-05-24
> **maaarg said:**
> Thanks--the workaround you suggested worked perfectly-- I suppose I can just use chmod to avoid having to type python2.7 every time, but should there be an easier way to do that?

As for your first suggestions:

got /usr/bin/python for the first command,

/usr/bin/python: symbolic link to `python2.6'  for the second

and the third showed python2.6 and python2.7 in the directory (I can give the actual response if that would be helpful).

Ok. Lets link the python executable to the version 2.7 file:```
sudo ln -s /usr/bin/python2.7 /usr/bin/python
```
Now, you should be able to use just python to execute the scripts using version 2.7 of python.

---

