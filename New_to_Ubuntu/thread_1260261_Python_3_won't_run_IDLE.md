---
title: "Python 3 won't run IDLE?"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by InfectedWithDrew on 2009-09-07
I downloaded and installed Python 3.1.1 on UNR 9.04 (everything up-to-date), however during installation I noticed that some modules didn't install correctly or something like that... I don't know how to fetch the output but if someone could tell me how to get it I'd be glad to fetch it.  Anyways, running python3 works fine, but running idle3 returns this error:
```
** IDLE can't import Tkinter.  Your Python may not be configured for Tk. **
```
Quite vexing, for I am taking a Python class and I kind of sorta really need IDLE to work.

Any help?

(And on a side note, how do I create an application launcher that appears in the main menu on UNR?)

Thanks in advance :D

---

### Post by Penguin Guy on 2009-09-07
[Isn't google wonderful?]("http://lmgtfy.com/?q=**+IDLE+can%27t+import+Tkinter.+%20Your+Python+may+not+be+configured+for+Tk.+**") Click [here]("apt:python3-tk") or run [COLOR="Green"]sudo apt-get install python3-tk[/COLOR].

---

### Post by InfectedWithDrew on 2009-09-09
> **Penguin Guy said:**
> [Isn't google wonderful?]("http://lmgtfy.com/?q=**+IDLE+can%27t+import+Tkinter.+%20Your+Python+may+not+be+configured+for+Tk.+**") Click [here]("apt:python3-tk") or run [COLOR="Green"]sudo apt-get install python3-tk[/COLOR].

This has solved nothing.  I get the same error.

---

### Post by InfectedWithDrew on 2009-09-10
Bump.  This is actually a pretty pressing issue.

---

### Post by Cheezespread on 2009-09-10
I just downloaded the tarball from the official Python page and installed the same from source. IDLE was in the repos and  i believe the package name was : idle-package3.0 . Installed the same . 

```
sudo aptitude install idle-python3.0
```

I didn't face any issues.

---

### Post by Mighty_Joe on 2009-09-10
> **InfectedWithDrew said:**
> however during installation I noticed that some modules didn't install correctly or something like that...  

That sounds like your problem right there.  Did you try removing Python and reinstalling?  That would probably fix whatever dependency has been screwed up.
Do you HAVE to use IDLE?  You can set up pretty much any text editor to correctly handle Python files (personally, I use [JEdit]("http://www.jedit.org/"), but Emacs, VI, gedit and thousands of others will work).

---

### Post by InfectedWithDrew on 2009-09-10
> **Cheezespread said:**
> I just downloaded the tarball from the official Python page and installed the same from source. IDLE was in the repos and  i believe the package name was : idle-package3.0 . Installed the same . 

```
sudo aptitude install idle-python3.0
```
This did not work :|

I didn't face any issues.

> **Mighty_Joe said:**
> That sounds like your problem right there.  Did you try removing Python and reinstalling?  That would probably fix whatever dependency has been screwed up.
Do you HAVE to use IDLE?  You can set up pretty much any text editor to correctly handle Python files (personally, I use [JEdit]("http://www.jedit.org/"), but Emacs, VI, gedit and thousands of others will work).I didn't have python installed before.  I mean, it was a fresh install of UNR...

And I don't know how to remove anything I install from source.  :\

But yeah, I do need IDLE.  It's for a class.  I know how to make .py files in text editors but we're sorta required to know IDLE for some reason.

---

### Post by Cheezespread on 2009-09-10
Python is installed by default in most Linux Operating systems. I reckon Vi , Emacs etc would do the same job as IDLE would do as a test editor. But i guess you specifically need IDLE. As he mentioned , could you try re-installing it ?

---

### Post by oldfred on 2009-09-11
I found on another site this comment on python 3.1, so this may be your problem?

module Tkinter it is renamed to tkinter

---

### Post by Mighty_Joe on 2009-09-12
> **InfectedWithDrew said:**
> 
And I don't know how to remove anything I install from source.  :\

Did you install with something like:
```

>configure
>make
>make install

```
?  There should be something like 
```
make uninstall
```
Check the root directory of the tarball for README files.  

> **InfectedWithDrew said:**
> 
But yeah, I do need IDLE.  It's for a class.  I know how to make .py files in text editors.

Speak to your instructor about your problem. Tell him/her you're working on getting IDLE going.  In any other text editor, you would save a Python file with a .py extension.  They aren't magic.  They're just text files that contain text instructions.

---

### Post by InfectedWithDrew on 2009-09-13
> **Cheezespread said:**
> Python is installed by default in most Linux Operating systems. I reckon Vi , Emacs etc would do the same job as IDLE would do as a test editor. But i guess you specifically need IDLE. As he mentioned , could you try re-installing it ?2.6 comes with Jaunty - not 3.1.

> **oldfred said:**
> I found on another site this comment on python 3.1, so this may be your problem?

module Tkinter it is renamed to tkinterHuh?  I can't even begin to follow you.

> **Mighty_Joe said:**
> Did you install with something like:
```

>configure
>make
>make install

```
?  There should be something like 
```
make uninstall
```
Check the root directory of the tarball for README files.  



Speak to your instructor about your problem. Tell him/her you're working on getting IDLE going.  In any other text editor, you would save a Python file with a .py extension.  They aren't magic.  They're just text files that contain text instructions.I understand - I've programmed with Python for a few months now.  I just wanted to have the python terminal and everything so I could keep up with the class... I didn't want to have to load files manually, rather than running then with F5... if I wanted to do that, hell, I'd use Java.

---

### Post by oldfred on 2009-09-13
I was just repeating what was said Tinker is not tinker as capitalization makes a difference. Whether it was an error or a change it breaks some things expecting Tinker.

I use Geany as it is easy to load multiple files easily run the modules while still in geany. Many suggest other editors but geany is one that works.

---

### Post by InfectedWithDrew on 2009-09-14
> **oldfred said:**
> I was just repeating what was said Tinker is not tinker as capitalization makes a difference. Whether it was an error or a change it breaks some things expecting Tinker.

I use Geany as it is easy to load multiple files easily run the modules while still in geany. Many suggest other editors but geany is one that works.

Your first part of advice still makes no sense.  But your second part does.  Duly noted, if it interprets Python and highlights syntax, then it sounds quite all right.

---

### Post by Mighty_Joe on 2009-09-14
> **InfectedWithDrew said:**
> if I wanted to do that, hell, I'd use Java.

That's funny. I'm a professional Java programmer. :lolflag:

---

### Post by InfectedWithDrew on 2009-10-05
I'm just going to bump this thread.

I talked to the New York State Ubuntu LoCo and they tried helping me but their advice hasn't worked.  I still can't run 'idle3'.  I get the same errors.  They had me try installing python3, but of course that didn't work.  I tried removing my manual install and reinstalling but that didn't work either.

Also, the universe has packages for 3.0.x, not 3.1.  So I need advice on getting the package to manually install correctly, or on getting the 3.1 package from the universe somehow, and getting THAT to install correctly.

Thanks in advance. :|

---

### Post by achase79 on 2009-10-05
If you really need python 3.1 you should look for a python 3.1 ppa on [http://launchpad.net]("http://launchpad.net").

---

### Post by InfectedWithDrew on 2009-10-05
> **achase79 said:**
> If you really need python 3.1 you should look for a python 3.1 ppa on [http://launchpad.net]("http://launchpad.net").It doesn't seem to exist.  I only found a project page.

---

### Post by mantis8 on 2009-10-26
I'm having a similar issue; I just recently got a new hdd and installed ubuntu 8.x & upgraded to 9.04.  I'm taking a beginning programming class (were not learning any particular language, just the general principles) and learning python on my own.  From system>administration>synaptic package manager, I was able to get tkinter installed, but cant seem to open it.  I tried r-clicking on the desktop and ran the launcher deal, but then have to search through dozens of directories, and scan through hundreds of files!  I don't know where to look. I tried usr>share>, usr>bin... and countless other directory/file combos; even if I do find an icon to use, I get some cryptic error. I tried to open from the command line, but got an error>> "open tkinter
Couldnt get a file descriptor referring to the console".  Why cant all apps in linux just put the launcher icon on the desktop by default?!?!?! :-x  Anyways, I'm having the same issue with other python apps like qt4 & pygtk and getting nowhere fast.  I was able to get boa constructor running, but was having other issues with that one. 

Any detailed help is appreciated.  

Gotta go to my programming class now.

---

### Post by Mighty_Joe on 2009-10-27
> **mantis8 said:**
> I was able to get tkinter installed, but cant seem to open it.  

[TkInter]("http://wiki.python.org/moin/TkInter") is a GUI library.  It is not an application.

> **mantis8 said:**
>  Why cant all apps in linux just put the launcher icon on the desktop by default

I assure you, if you developed an application and configured it to put an icon on the desktop, you'd be flooded with angry emails from people who want to know why you are cluttering their desktops.

---

### Post by mantis8 on 2009-10-27
Thx for info.  At least when software is installed, a pop up box should come up & give you the option to check a box and have the launcher icon put on the desktop.  How long does that take? 1 second!  I have spent several hours over the past week or so just trying to get access to ONE piece of software.  

I found an excellent url here: [http://wiki.python.org/moin/GuiProgramming](http://wiki.python.org/moin/GuiProgramming).  I'm interested in rapid application development (RAD). I would really like to just point & click my way to make a nice gui, then hand code the rest, but if I have to do it all from scratch by hand, I will.  

My problem is that I cant seem to (get access to, open, run, etc) any piece of development software.  I'm ready to pay somebody who can give me the correct answer. This cant be rocket science.  I dont care if I have to use the CLI; I just need to get going. This has been a huge productivity killer.  I dont know where the correct file is to link to with the launch deal.  Preferably, I'd also like to be able to use the latest version of python (3.1.1?) and just start off with the newest version.  

I've got pygtk installed & unpacked it, but don't know what to do from here.

---

### Post by Mighty_Joe on 2009-10-27
> **mantis8 said:**
> I've got pygtk installed & unpacked it, but don't know what to do from here.

Again, pygtk is a GUI library, specifically, Python bindings to the GTK toolkit.  It is not an application.  
Frankly, in order to understand "rapid application development", one should first understand "application development".  I've seen many beginning programmers take a whiz-bang GUI builder and slap together some really horrendous code that they have no hope of unraveling, understanding or getting to work.
My advice: start with the basics.  Once you have a solid foundation, it will be easy to add new skills.  Start by downloading [Think Python]("http://www.greenteapress.com/thinkpython/").  Ubuntu comes with Python 2.6.2, which is a perfectly fine release for learning (I have plenty of scripts written for it that run fine in Python 3.x).  Once you get a solid grasp of Python's basics, try writing GUI code.

---

### Post by HarrisonNapper on 2009-10-27
1. Ensure a version of python is installed (I use 2.5)
2. Type "python" in to a terminal
3. ????
4. PROFIT!!!

It looks like you might be trying to use an IDLE GUI, so this may not help you there, but the terminal version of IDLE worked just fine for me in learning the basics of python (see previous posts by Mighty_Joe) and it should be sufficient for keeping up in class.

Cheers.

---

### Post by screaminfakah on 2009-10-27
I would try to install the 3.0.x from Synaptic so it will install the dependencies. You will also have to install Idle as Synaptic will not select it for you since Python is not dependent on Idle for it to work. 
There cant be that big of a difference between that and 3.1. You probably wont even notice a difference.

---

