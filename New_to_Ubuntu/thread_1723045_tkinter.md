---
title: "tkinter"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by mdavidjohnson on 2011-04-06
I've checked these forums, the Community Documentation, and the ubuntu Lucid Documentation and can't seem to find a fix for this - it's pretty obvious that I'm simply not getting something.

I'm running python 3.2 under ubuntu 10.04 on a Pentium D. I'm also running it under Windows 7 Pro 64-bit on an AMD64 Phenom.

The following code works perfectly under Win7:

```

#-----
# gui01.py
# MDJ 2011/04/06
# cf. Programming Python, p. 368

from tkinter import Label                       # get a widget object
widget = Label(None, text='Hello GUI World!')   # make one
widget.pack()                                   # arrange it
widget.mainloop()                               # start event loop
#-----

```

But when I tried it under ubuntu, it failed, saying there was no module named tkinter. Figuring it was just something that hadn't come with the python package, I tried:

sudo apt-get install tkinter

But the response said no such package exists.

So I looked through the Lucid packages repository and found that python-tk was listed as the Tkinter provider. So I tried:

sudo apt-get install python-tk

That worked. But when I tried to run gui01.py it still said there was no module named tkinter.

I tried changing:

```

from tkinter import Label			# get a widget object

```

to:

```

from Tkinter import Label			# get a widget object

```

and to:

```

from python-tk import Label			# get a widget object

```

But, neither one worked. The second seemed to import the Label but then the widget assignment statement failed.

What am I doing wrong?

---

### Post by charlie_b on 2011-04-06
In your import statement Tkinter should be capitalised. Try this:

from Tkinter import *
root=Tk()
widget=Label(root, text='Hello World')
widget.pack()
root.mainloop()

---

### Post by GWBouge on 2011-04-06
> **charlie_b said:**
> In your import statement Tkinter should be capitalised.

Not for Python3 it seems.  I generally use wxPython, which doesn't support Python3 just yet, but out of curiosity I tried what the OP is suggesting ...

```
bummer@bummer-desktop:~$ python
Python 2.6.6 (r266:84292, Sep 15 2010, 16:22:56) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from Tkinter import *
>>> exit()
bummer@bummer-desktop:~$ python3
Python 3.2 (r32:88445, Apr  3 2011, 17:20:59) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from Tkinter import *
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named Tkinter
>>> from tkinter import *
Traceback (most recent call last):
  File "/usr/lib/python3.2/tkinter/__init__.py", line 40, in <module>
    import _tkinter
ImportError: No module named _tkinter

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python3.2/tkinter/__init__.py", line 42, in <module>
    raise ImportError(str(msg) + ', please install the python-tk package')
ImportError: No module named _tkinter, please install the python-tk package
>>> 
```

Yes, python-tk is installed.

---

### Post by lebastidien09 on 2011-07-15
python-tk on Ubuntu seems to work with python2
Try to install python3-tk :
[FONT=Courier New]
sudo apt-get install python3-tk[/FONT]

---

### Post by skitz2009 on 2012-03-08
Pls. advise how to resolve the issue below:

$ ./**sample1.py**
Traceback (most recent call last):
  File "./sample2.py", line 3, in <module>
    from Tkinter import *
  File "/usr/lib/python2.6/lib-tk/Tkinter.py", line 42, in <module>
    raise ImportError, str(msg) + ', please install the python-tk package'
ImportError: [COLOR=Red]No module named _tkinter, **please install the python-tk package**[/COLOR]


$ python
**Python 2.6.6 **(r266:84292, Sep 15 2010, 15:52:39) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>

---

