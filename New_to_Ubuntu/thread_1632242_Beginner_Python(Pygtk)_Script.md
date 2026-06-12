---
title: "Beginner Python(Pygtk) Script"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by Stigmata13 on 2010-11-27
Hello. I've recently started to learn python (pygtk mostly) and I've been playing around with scripts. I've managed to write one, but I can't get it to run. Here's the script:

```

import gtk
window = gtk.Window()
window.resize(800,600)
window.set_title("Patrick's Web Browser")
import webkit
browser = webkit.WebView()
scroller = gtk.ScrolledWindow()
scroller.add(browser)
window.add(scroller)
browser.open("http://www.google.com")
window.show()
browser.show()
scroller.show()

```
I managed to write it after watching a video on tuxradar. When entering the terminal and typing "python" and then typing the commands one by one, at the end I get what I wrote (a page with google open, with a scrollbar.)
However, I can't get it to run outside of python in the terminal. I have it saved as Test1.py, and I've tried navigating to the directory and typing "python Test1.py", but it doesn't do anything, and just goes to a new terminal line without bringing up any windows.
What am I doing wrong? I'm currently using Geany for my IDE, although I don't know how to use it except for writing the code and saving it as .py

Any help would be appreciated!

---

### Post by Foxheadz on 2010-11-27
At the top of your file add #!/usr/bin/python and right click on the file and under permission add execute. Now it should run

---

### Post by Stigmata13 on 2010-11-27
> **Foxheadz said:**
> At the top of your file add #!/usr/bin/python and right click on the file and under permission add execute. Now it should run

Thanks! After doing that it seems to recognize it as a python script.
However, it still doesn't want to show anything. Even after giving it proper permissions, it seems like it launches but nothing comes up.
Is there anything else I'm missing? These commands ran great in the terminal after running python from there and typing them in line by line.
Is it possible that since it's a script, it just runs everything and then closes (hence, why I don't see it?)

---

### Post by Foxheadz on 2010-11-27
Yeah that would make sense im also sort of new to python so i don't really know a solution to that

---

### Post by Stigmata13 on 2010-11-28
Bump... still looking for a solution :D
Any help or advice would be much appreciated.

---

### Post by asmoore82 on 2010-11-28
I'm new to pygtk as well.

Graphical apps are inherently multi-threaded and/or event-driven.
You need to pass execution over to the gtk.main thread.

This creates the opposite problem, the script never stops even after the window is closed!
To fix this, you have to attach an event callback function to closing the window.

Here is a very rough fix:
```
#!/usr/bin/env python
#pybrowser.py

import gtk
import webkit

def on_close(*args):
    gtk.main_quit()

window = gtk.Window()
window.connect("delete_event", on_close)
window.resize(800,600)
window.set_title("Patrick's Web Browser")

browser = webkit.WebView()
scroller = gtk.ScrolledWindow()
scroller.add(browser)
window.add(scroller)
browser.open("http://www.google.com")

window.show()
browser.show()
scroller.show()

gtk.main()

#End of File
```

---

### Post by asmoore82 on 2010-11-28
I think the next step is to get object oriented:

```
[COLOR="Blue"]#!/usr/bin/env python
#pybrowser.py[/COLOR]

import gtk
import webkit

class MyBrowser:
    def __init__(self, name='Adam'):
[COLOR="Blue"]        #Create instance objects[/COLOR]
        self.name = name
        self.window = gtk.Window()
        self.scroller = gtk.ScrolledWindow()
        self.browser = webkit.WebView()
        
[COLOR="Blue"]        #Set window properties[/COLOR]
        self.window.resize(800, 600)
        self.window.set_title(self.name + "'s Web Browser")

[COLOR="Blue"]        #Pack widgets[/COLOR]
        self.scroller.add(self.browser)
        self.window.add(self.scroller)
        self.browser.open("http://www.google.com")

[COLOR="Blue"]        #Show all[/COLOR]
        self.browser.show()
        self.scroller.show()
        self.window.show()

[COLOR="Blue"]        #Connect signals[/COLOR]
        self.window.connect("delete_event", self.on_delete)

    def main(self):
        gtk.main()

    def on_delete(self, widget, *args):
        gtk.main_quit()


if __name__ == "__main__":
    browser = MyBrowser()
    browser.main()

[COLOR="Blue"]#End of File[/COLOR]
```

This is runnable as a script but also lets you do this:
```
python
>>> from pybrowser import *
>>> test1 = MyBrowser()
>>> test2 = MyBrowser('Patrick')
```

You should check out Quickly! [https://wiki.ubuntu.com/Quickly](https://wiki.ubuntu.com/Quickly)

---

### Post by Stigmata13 on 2010-11-28
Thanks a lot, asmoore82. That did the trick!
Looks like I still have quite a lot more to learn. :D

---

