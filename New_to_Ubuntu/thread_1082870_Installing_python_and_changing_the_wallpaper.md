---
title: "Installing python and changing the wallpaper"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by FLMKane on 2009-02-28
I been having a few problems with my Ubuntu 8.10 OS, definately because I'm a linux noob. I've been using Ubuntu since the end of January, and I'll admit it has'nt been without a hitch. I could'nt get it to run on my old minimum specs P4, but fortunately I could use Ubuntu as soon as I bought a new one. I'm very happy with its capabilities.

However I cant figure out how to install Python 2.6 on my Ubuntu :(. There has got to be a better way to install it besides compiling the source codes. If there is'nt how do I compile it anyway? I'm a programming n00b too.

Besides that, I really would like to use a different wallpaper. I can change it temporarily but every time I restart the system it changes back to the Intrepid Ibex wallpaper.

---

### Post by ptn107 on 2009-02-28
The developers are currently transitioning 9.04 from python 2.5 to 2.6.  You will either have to wait for 9.04 in April or attempt to compile python from source.

---

### Post by FLMKane on 2009-02-28
How do you compile it from source?

---

### Post by lordharsha on 2009-02-28
$wget [http://www.python.org/ftp/python/2.6.1/Python-2.6.1.tgz](http://www.python.org/ftp/python/2.6.1/Python-2.6.1.tgz)
$tar xzf Python-2.6.1.tgz
$cd Python-2.6.1
$sudo python setup.py install

A quick explanation of what you'll be doing.

wget downloads the file. It's the same as downloading a file from a web browser.

tar extracts the file, similar to right clicking on the file and selecting Extract Here. As for the options, x is for extract, z identifies the file as a .gz file, and f creates a folder for it.

cd changes the current directory.

python setup.py install runs the python installation script.

As for the wallpaper, it's possible that the image file is being moved after being set as the wallpaper. I doubt it's the cause, but it's the only thing I can think of.

---

### Post by oldos2er on 2009-02-28
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by FLMKane on 2009-03-01
I got an error 

nabeel@ubuntu:~/Python-2.6.1$ sudo python setup.py install
running install
running build
running build_ext
error: pyconfig.h: No such file or directory

---

