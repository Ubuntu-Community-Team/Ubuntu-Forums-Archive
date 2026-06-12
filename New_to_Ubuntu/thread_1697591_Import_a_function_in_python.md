---
title: "Import a function in python"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by hdanap on 2011-03-01
Hi Everybody,

I'm python learning, and in my book, it just tell me to import a function I wrote into python to see the function work, but when i import the function with

from script_name import *

function_name()

i get told no module like that exists,

I read some where i have to include the path in ubuntu, i have no clue what how to include the path to python or what i should be doing to import the function.

Pls assist.

Thanks

---

### Post by Smart Viking on 2011-03-01
Hello.

If you launch the python interpreter from the same directory as the module you created, you can import it. Lets say example that I am located in my home directory, and in there I have a module with a function "omg", and the name of it is "omg.py". If I lauch the interpreter, I can go ahead and type
```
>>> from omg import *
>>> omg()
```And it will work. Now if I want to import a module from somewhere else, one way you can do that and I don't know if it's the best way but that's how I did it, is by importing sys and modifying sys.path:
```
>>> import sys
>>> sys.path
['', '/usr/lib/python2.6', '/usr/lib/python2.6/plat-linux2', '/usr/lib/python2.6/lib-tk', '/usr/lib/python2.6/lib-old', '/usr/lib/python2.6/lib-dynload', '/usr/local/lib/python2.6/dist-packages', '/usr/lib/python2.6/dist-packages', '/usr/lib/python2.6/dist-packages/gst-0.10', '/usr/lib/pymodules/python2.6', '/usr/lib/pymodules/python2.6/gtk-2.0']
>>> sys.path = sys.path + ['/home/smartviking']
>>> sys.path
['', '/usr/lib/python2.6', '/usr/lib/python2.6/plat-linux2', '/usr/lib/python2.6/lib-tk', '/usr/lib/python2.6/lib-old', '/usr/lib/python2.6/lib-dynload', '/usr/local/lib/python2.6/dist-packages', '/usr/lib/python2.6/dist-packages', '/usr/lib/python2.6/dist-packages/gst-0.10', '/usr/lib/pymodules/python2.6', '/usr/lib/pymodules/python2.6/gtk-2.0', '/home/smartviking']

```As you can see, that worked, now I can go ahead and import any modules from my home directory, and use it's code.

EDIT
For the record, this seems to also work:
```
>>> sys.path = sys.path + ['/home/$HOME']
```

---

### Post by hdanap on 2011-03-01
Sweet, that took care of my problem, both method worked.

Thanks for the assist.

---

