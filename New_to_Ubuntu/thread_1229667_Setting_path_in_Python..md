---
title: "Setting path in Python."
date: 2009-08-02
forum: New to Ubuntu
---

### Post by BardSeed on 2009-08-02
I am attempting to learn python, and have taken a few lessons from a free online tutorial. The tutorial is written for windows. Things were going fine, but I've come to a point where I'm not sure what I'm supposed to do.

Here is what I'm told to do "You will need to cause the directory containing the file named python.exe to be listed in your system environment variable named path." If you could help me understand what this means and how to do it, I'd be very grateful. 

I have performed a short search, both on Google and here, but didn't find what I was looking for. It doesn't help that I'm not exactly sure what's being asked of me.

This is the page I'm using. [http://www.dickbaldwin.com/python/Pyth0016.htm](http://www.dickbaldwin.com/python/Pyth0016.htm)
I'm running ubuntu 8.04, if that's important.

---

### Post by llamabr on 2009-08-02
Hi.  I'm no python expert, but I know your version doesn't come with a python.exe

Why don't you find a tutorial that's specific to your own os?

[http://linux.wareseeker.com/free-python-tutorial/](http://linux.wareseeker.com/free-python-tutorial/)

---

### Post by bruce2000 on 2009-08-02
Hi,

If you're using Ubuntu then Python will already be in your system path, there's no need to set the environment variable like in Windows.

What it does it let you execute the command "python" in a terminal no matter what your current directory is. Or another way of looking at it - you can type "python yourprogram" for it to run, without the need to qualify the path to the Python executable.

I think you can just ignore this part of your tutorial; it's for Windows only.

---

### Post by BardSeed on 2009-08-02
> **bruce2000 said:**
> Hi,

If you're using Ubuntu then Python will already be in your system path, there's no need to set the environment variable like in Windows.

What it does it let you execute the command "python" in a terminal no matter what your current directory is. Or another way of looking at it - you can type "python yourprogram" for it to run, without the need to qualify the path to the Python executable.

I think you can just ignore this part of your tutorial; it's for Windows only.

Thanks for clearing that up. I was confused when I found the python files without their own directory.

---

