---
title: "Glade on Lucid"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by vivek40 on 2010-07-18
Hi have just started learning and working on Glade. Installed Glade yesterday from the repositories.Created a very simple interface with a window , a vertical box and two buttons. Then once the XML file was created , I created the python script in the same directory but on running it It get these Errors
```

(VivButtons.py:3263): libglade-WARNING **: Expected <glade-interface>.  Got <interface>.

(VivButtons.py:3263): libglade-WARNING **: did not finish in PARSER_FINISH state
Traceback (most recent call last):
  File "VivButtons.py", line 9, in <module>
    Buttons()
  File "VivButtons.py", line 6, in __init__
    self.window = gtk.glade.XML('VivButtons.glade', 'window1')
RuntimeError: could not create GladeXML object

```The python script to use the XML file is as below:-
```

#!/usr/bin/env python
import pygtk
import gtk
import gtk.glade
class Buttons:
    def __init__(self):
        self.window = gtk.glade.XML('vivbuttons.glade', 'window1')

if __name__ == '__main__':
    Buttons()
    gtk.main()

```The XML file is here [http://paste.pocoo.org/show/239003/ ]("http://paste.pocoo.org/show/239003/")


n.b-the glade version is 3.6.7
[ ]("http://paste.pocoo.org/show/239003/")

---

### Post by oldfred on 2010-07-18
Glade will output either the older glade format or the newer builder format, both are XML files but the code in python is different.

builder definitions
[http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html](http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html)
builder
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)
py faqs builder
[http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp](http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp)

---

### Post by vivek40 on 2010-07-19
Hi I guess I need to install libgtk2.0-dev for converting the glade file , bt when I try to install it, *I get the *following error. Can someone help me with this:-

```

vivek@vivek-desktop:~/myprogs/learningpython$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.20.1-0ubuntu2) but 2.20.1-0ubuntu3~10.04~ricotz1 is to be installed
                 Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.13.0) but it is not going to be installed
E: Broken packages


```

---

### Post by Legendary_Bibo on 2010-07-19
> **vivek40 said:**
> Hi I guess I need to install libgtk2.0-dev for converting the glade file , bt when I try to install it, *I get the *following error. Can someone help me with this:-

```

vivek@vivek-desktop:~/myprogs/learningpython$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.20.1-0ubuntu2) but 2.20.1-0ubuntu3~10.04~ricotz1 is to be installed
                 Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.13.0) but it is not going to be installed
E: Broken packages


```

It means you have to find and install those packages. Try looking in Synaptic, if not then google them.

---

### Post by vivek40 on 2010-07-19
Thanks OldFred! I guess I was able to solve it finally by spending some time on all those links!

---

