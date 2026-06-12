---
title: "Trying to install Marave"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by Greenwick on 2011-07-24
I'm trying to install Marave, a program which is like OmmWriter.  This is the first program I've tried to install that isn't available in the Ubuntu Software Center, so I'm a bit lost.  I am learning more about Ubuntu, though, so I think I can handle it as soon as I know what direction to head.

(Edited:  I tried following the advice of [this page]("http://www.omgubuntu.co.uk/2010/08/marave-distraction-free-writing-in-linux/"), and this is what it said:

greenwick@greenwick-1001PX:~$ sudo python setup.py install
python: can't open file 'setup.py': [Errno 2] No such file or directory)


The page for Marave is [here.]("http://code.google.com/p/marave/")  It says that Ubuntu users will have to use the source, which I wasn't able to open.  

I'm thinking the 'set up' folder is the place to start, and that I should enter what it says into the terminal.  I don't want to screw anything up royally, so I wanted to ask here first. Here are its contents:

```
# -*- coding: utf-8 -*-

from distutils.cmd import Command
from distutils.core import setup, Extension
import os

class build_hl(Command):
    """Builds the syntax highlighter extension"""
    user_options = []
    description = "Build the syntax highlighter extension"
    
    def initialize_options(self):
        self._dir = os.path.abspath(os.path.dirname(__file__))

    def finalize_options(self):
        pass    
    
    def run(self):
        os.chdir(os.path.join(self._dir,'marave','editor','highlight'))
        r=os.system('python configure.py')
        if r==0:
            os.system('make')
        os.chdir(self._dir)

setup(name='Marave',
      version='0.7',
      description='A relaxed text editor',
      author='Roberto Alsina',
      author_email='ralsina@netmanagers.com.ar',
      url='http://marave.googlecode.com',
      packages=['marave',
                'marave.editor',
                'marave.editor.widgets',
                'marave.plugins'],
      scripts=['marave-editor'],
      package_data={'marave': ['backgrounds/*',
                               'icons/*svg',
                               'clicks/*wav',
                               'themes/*',
                               'stylesheets/*',
                               'translations/*',
                               'highlight/*',
                               'editor/highlight/*',
                               'radios.txt'
                               ]},
     cmdclass = { 'build_hl': build_hl },
     )
```
Thanks!

---

### Post by gigenieks on 2011-07-24
I suggest edit your post by putting that code in #tags.
Like this --->
```

# -*- coding: utf-8 -*-

from distutils.cmd import Command
from distutils.core import setup, Extension
import os

class build_hl(Command):
"""Builds the syntax highlighter extension"""
user_options = []
description = "Build the syntax highlighter extension"

def initialize_options(self):
self._dir = os.path.abspath(os.path.dirname(__file__))

def finalize_options(self):
pass 

def run(self):
os.chdir(os.path.join(self._dir,'marave','editor', 'highlight'))
r=os.system('python configure.py')
if r==0:
os.system('make')
os.chdir(self._dir)

setup(name='Marave',
version='0.7',
description='A relaxed text editor',
author='Roberto Alsina',
author_email='ralsina@netmanagers.com.ar',
url='http://marave.googlecode.com',
packages=['marave',
'marave.editor',
'marave.editor.widgets',
'marave.plugins'],
scripts=['marave-editor'],
package_data={'marave': ['backgrounds/*',
'icons/*svg',
'clicks/*wav',
'themes/*',
'stylesheets/*',
'translations/*',
'highlight/*',
'editor/highlight/*',
'radios.txt'
]},
cmdclass = { 'build_hl': build_hl },
)

```

Much easier to read. :)

As for installing can't give specific solutions etc, but you should find [[COLOR="DarkGreen"]**_something here (click on me)_**[/COLOR]]("https://help.ubuntu.com/community/InstallingSoftware")

---

### Post by Greenwick on 2011-07-25
Thanks for the tip.  I was wondering how people made small scrollable sections of posts.

---

