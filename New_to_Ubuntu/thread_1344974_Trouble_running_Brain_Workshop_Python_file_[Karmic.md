---
title: "Trouble running Brain Workshop Python file [Karmic]"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by IrenicBright on 2009-12-03
I recently downloaded the linux version of Brain Workshop 4.4 from [http://brainworkshop.sourceforge.net/osx-linux.html#linux](http://brainworkshop.sourceforge.net/osx-linux.html#linux).

Following their instructions I unzipped the file, opened the terminal, changed to the Brain Workshop directory and then typed:
```
python brainworkshop.pyw
```

This resulted in the following:
Traceback (most recent call last):
  File "./brainworkshop.pyw", line 712, in <module>
    window = MyWindow(WINDOW_WIDTH, WINDOW_HEIGHT, caption=''.join(caption), style=style, vsync=VSYNC)
  File "/home/adam/Downloads/brainworkshop/pyglet/window/xlib/__init__.py", line 474, in __init__
    super(XlibWindow, self).__init__(*args, **kwargs)
  File "/home/adam/Downloads/brainworkshop/pyglet/window/__init__.py", line 626, in __init__
    display = get_platform().get_default_display()
  File "/home/adam/Downloads/brainworkshop/pyglet/window/xlib/__init__.py", line 152, in get_default_display
    return self.get_display('')
  File "/home/adam/Downloads/brainworkshop/pyglet/window/xlib/__init__.py", line 148, in get_display
    self._displays[name] = XlibDisplayDevice(name)
  File "/home/adam/Downloads/brainworkshop/pyglet/window/xlib/__init__.py", line 166, in __init__
    raise NoSuchDisplayException('Cannot connect to "%s"' % name)
pyglet.window.NoSuchDisplayException: Cannot connect to ""

Since my first attempt I have tried using Brain Workshop versions 4.3 and 4.5 with the same results. I am running Python 2.6.4 and Ubuntu 9.10. I've never tried to run a .pyw file before this and haven't had any luck searching google for similar errors.

What could be going on here? Any pointers would be much appreciated.

---

### Post by DaithiF on 2009-12-03
hello,
in the terminal, before running the python command, try:
```
export DISPLAY=:0.0
```
then run the python command as before

---

### Post by IrenicBright on 2009-12-04
Thanks! That worked great.

Could you possibly explain why the export command worked? At first I thought this might be an issue with my nvidia drivers (they have caused me a bit of grief with 9.10), but my girlfriend gets the same error on her intel laptop.

---

### Post by DaithiF on 2009-12-04
Hi, many graphical programs in linux/unix rely on the DISPLAY variable to figure out which X server to talk to when displaying graphics.  Normally DISPLAY is set for you when your graphical environment is started at login (via. startx).  I don't know why yours isn't getting set, or perhaps it is, but something in your bash profile is causing it to be unset when you launch a terminal.  If you don't ssh into your computer (ie. you don't use it remotely) then you can just add the export display command above to your .bashrc file and you should be ok.

---

