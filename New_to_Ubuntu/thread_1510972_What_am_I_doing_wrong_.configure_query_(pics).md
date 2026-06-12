---
title: "What am I doing wrong? /.configure query (pics)"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by ZenFeedbacker on 2010-06-16
Hey there, I recently installed Jolicloud's Pre-Final on my Nokia Booklet 3g. This is only the second time I've ever used Linux, and I remember very little from the last time I did!
I've enclosed a screenshot showing (I think) all the information you guys need in order to work out what I might be doing wrong here. I've read numerous threads on this subject, but none have hit the nail on the head, if that makes sense. So rather than try to apply the knowledge I'm picking up from other people's difficulties with Tar.gz unpacking and installation, I must resort to a bespoke enquiry. :)
I'm trying to install Marave text editor, and while the unpacking went well - I can't seem to kick the proceeding steps of /.configure, make - etc. into action. Regardless of my attempts, I receive this error, "bash: /.configure: No such file or directory" as you can see from the Terminal in my image. 
Can anybody see what I'm doing wrong? :]
Here's a link to the image (didn't want to risk a loss of fidely by auto-resizing): [http://img51.imageshack.us/img51/948/screenshotfd.png](http://img51.imageshack.us/img51/948/screenshotfd.png)

---

### Post by tarps87 on 2010-06-16
The answer is in the document to the right
"To install from sources try this:
python setup.py install"

Have you tried this?
the configure command is part of a compilation process however this project does not use this process instead it relies on a python script.
If you do not have python installed it is available through the package manager

---

### Post by ZenFeedbacker on 2010-06-16
Thanks for that, I'll try that out now. :)

---

### Post by Irony on 2010-06-16
Simpler still just right click on marave-editor and choose permissions and make it executable.

Then either double click on it or drag it into terminal and hit enter - it should run straight away. You can decide were to put the program later...

---

### Post by ZenFeedbacker on 2010-06-16
Okay so,
I tried to install Python, I then unpacked it and again failed to configure it (I'm an idiot.).

I also tried your suggestion Irony - but I didn't understand what permissions to choose, I didn't understand whether to Run, Display or Run in Terminal, and upon try all 3 - none worked for some reason. :(

---

### Post by nothingspecial on 2010-06-16
It`s the chmod +x bit in the right hand window.

---

### Post by Irony on 2010-06-16
Stop trying to configure... there is nothing to configure!!!

Its all ready to run as it is. Do as I said and right click on marave-editor and choose permissions and make it executable.

Then either double click on it or drag it into terminal and hit enter - it should run straight away. You can decide were to put the program later...

---

### Post by PriceChild on 2010-06-16
**_To install:_**
In a terminal, run the following two commands.
```

sudo apt-get install python-setuptools python-qt4
sudo easy_install marave

```

**_To run:_**
```

marave-editor

```

Let me know how it goes!

---

### Post by ZenFeedbacker on 2010-06-16
> **Irony said:**
> Stop trying to configure... there is nothing to configure!!!

Its all ready to run as it is. Do as I said and right click on marave-editor and choose permissions and make it executable.

Then either double click on it or drag it into terminal and hit enter - it should run straight away. You can decide were to put the program later...

I appreciate that insofar as you clearly know more than me about this - however, what you're suggesting for me doesn't work sadly. 'It should run straight away', except it doesn't. Nothing happens. Jolicloud asks me if I want to Run, Display or Run in Terminal. None of those three options results in success. :/

---

### Post by Irony on 2010-06-16
Yup, from synaptic install python-qt4 first - then drag marave-editor into terminal and run it (after making it executable).

---

### Post by Irony on 2010-06-16
> **ZenFeedbacker said:**
> however, what you're suggesting for me doesn't work sadly. 'It should run straight away'
Yes it does, I've just tried it - drag marave-editor into terminal (after making it executable). Note install python-qt4 from synaptic first.

---

### Post by ZenFeedbacker on 2010-06-16
> **PriceChild said:**
> **_To install:_**
In a terminal, run the following two commands.
```

sudo apt-get install python-setuptools python-qt4
sudo easy_install marave

```

**_To run:_**
```

marave-editor

```

Let me know how it goes!

```
sudo apt-get install python-setuptools python-qt4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-qt4 is already the newest version.
The following packages were automatically installed and are no longer required:
  xulrunner-1.9.1-gnome-support
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  python-setuptools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 195kB of archives.
After this operation, 909kB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com jaunty/main python-setuptools 0.6c9-0ubuntu4 [195kB]
Fetched 195kB in 1s (178kB/s)         
Selecting previously deselected package python-setuptools.
(Reading database ... 117158 files and directories currently installed.)
Unpacking python-setuptools (from .../python-setuptools_0.6c9-0ubuntu4_all.deb) ...
Setting up python-setuptools (0.6c9-0ubuntu4) ...

zenfeedbacker@Krishna:~$ sudo easy_install marave
Searching for marave
Best match: Marave 0.7
Adding Marave 0.7 to easy-install.pth file

Using /usr/local/lib/python2.6/dist-packages
Processing dependencies for marave
Finished processing dependencies for marave
zenfeedbacker@Krishna:~$ marave-editor
Traceback (most recent call last):
  File "/usr/local/bin/marave-editor", line 5, in <module>
    from marave.main import main
  File "/usr/local/lib/python2.6/dist-packages/marave/main.py", line 58, in <module>
    from editor import Editor
  File "/usr/local/lib/python2.6/dist-packages/marave/editor/__init__.py", line 3, in <module>
    from spelltextedit import Editor
  File "/usr/local/lib/python2.6/dist-packages/marave/editor/spelltextedit.py", line 38, in <module>
    from PyQt4.QtCore import pyqtSignal
ImportError: cannot import name pyqtSignal
```

---

### Post by PriceChild on 2010-06-16
As a side note, its *./configure*, not */.configure*. You shouldn't be using either of those though.

Please look at my earlier post! :-)

---

### Post by ZenFeedbacker on 2010-06-16
> **PriceChild said:**
> As a side note, its *./configure*, not */.configure*. You shouldn't be using either of those though.

Please look at my earlier post! :-)

I'll bear that in mind, cheers :]
As for looking at your earlier post - I did, you said to tell you how it went, I showed you ^
heh :) I don't think it worked. Can you see in that terminal code where the fault is?

---

### Post by PriceChild on 2010-06-16
Sounds like a bug in the marave code to me... good news... googling the error brings this thread up 2nd already.

I'll have another look for you.

---

### Post by pmlxuser on 2010-06-16
I thought its "./configure " and not  "/.configure"

Oh i guess am late with this observation

---

### Post by ZenFeedbacker on 2010-06-16
> **PriceChild said:**
> Sounds like a bug in the marave code to me... good news... googling the error brings this thread up 2nd already.

I'll have another look for you.

Greatly appreciated :)
I'm a writer, and having experienced the Ommwriter application (available currently only on Mac) I have a great desire to emulate that sort of program on my Jolicloud OS - and Marave appears to be the only option.

---

