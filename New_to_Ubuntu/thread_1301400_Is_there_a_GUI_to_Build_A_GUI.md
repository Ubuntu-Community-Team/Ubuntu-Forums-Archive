---
title: "Is there a GUI to Build A GUI?"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by nakama85 on 2009-10-26
I know that it seems like a dumb question but I figured I would ask and maybe someone would surprise me. I am looking to make a front end for something like wget (just to try it out). I know a couple already exist for wget I just want to use it as something to start with in order to learn the ropes.

Thanks

---

### Post by jbrown96 on 2009-10-26
You could use qtdesigner or qtcreator. I'm not sure what programming languages you know, but qtdesigner supports many including c++ and python.

---

### Post by nakama85 on 2009-10-26
> **jbrown96 said:**
> You could use qtdesigner or qtcreator. I'm not sure what programming languages you know, but qtdesigner supports many including c++ and python.

Thanks! I am really not programing intelligent yet. I am looking to start to learn. My starting goal is to make a little front end for wget that basically just has you paste the url - Select Where To Save - And allow you to choose a couple parameters. and send the output to the terminal 

Any Thoughts on where to start?

---

### Post by diesch on 2009-10-26
For really simple things just a shell script using zenity may be enough:

```
#!/bin/sh

url="$(zenity --entry --title='Enter URL' --text='Enter the URL you want to download:')" || exit 1
dir="$(zenity --file-selection --title='Select destination'  --directory --filename='.' )" || exit 1

wget -P "$dir" "$url"

```

If you want to start real programming Python could be a good language to start with, see [http://wiki.python.org/moin/BeginnersGuide/NonProgrammers](http://wiki.python.org/moin/BeginnersGuide/NonProgrammers) for a list of tutorials.

---

### Post by nakama85 on 2009-10-26
> **diesch said:**
> For really simple things just a shell script using zenity may be enough:

```
#!/bin/sh

url="$(zenity --entry --title='Enter URL' --text='Enter the URL you want to download:')" || exit 1
dir="$(zenity --file-selection --title='Select destination'  --directory --filename='.' )" || exit 1

wget -P "$dir" "$url"

```

If you want to start real programming Python could be a good language to start with, see [http://wiki.python.org/moin/BeginnersGuide/NonProgrammers](http://wiki.python.org/moin/BeginnersGuide/NonProgrammers) for a list of tutorials.

and for my next dumb question! How Would I apply this script. ie: where do I save it and what do I save it as, etc!

---

### Post by jbrown96 on 2009-10-26
I highly recommend Python as well. I don't think you should start programming with something so ambitious. Creating GUIs, creating/reading sockets, and doing file I/O is not easy. If you don't have any programming experience, you should pick up a Python book and work through it. [This is a great book]("http://www.amazon.com/Object-Oriented-Programming-Python-Michael-Goldwasser/dp/0136150314") that I used in my python class. Granted the authors are my professors, but it's really good. They have created a really good graphics system, so it can make programming a little more entertaining. 


I don't want to dash your hopes, but I think you should learn the basics first.

---

### Post by Paqman on 2009-10-26
> **nakama85 said:**
> and for my next dumb question! How Would I apply this script. ie: where do I save it and what do I save it as, etc!

You can save it anywhere you like, just make sure it's executable.

---

### Post by nakama85 on 2009-10-26
> **jbrown96 said:**
> ..."I don't think you should start programming with something so ambitious. Creating GUIs, creating/reading sockets, and doing file I/O is not easy."..."you should pick up a Python book and work through it. [great book]("http://www.amazon.com/Object-Oriented-Programming-Python-Michael-Goldwasser/dp/0136150314")"...

Thanks for the advice! I will definitely look into that. It just goes to show you how naive I am when it comes to programing. I truly thought that what I wanted to do was basic. I guess I was mistaken.  > **jbrown96 said:**
> I don't want to dash your hopes, but I think you should learn the basics first. no worries, if anything I am just more determined now!!

Thanks again

---

### Post by nakama85 on 2009-10-26
> **Paqman said:**
> You can save it anywhere you like, just make sure it's executable.

I made it executable but I get the following error when I click on it.

```
Could not display "/home/uname/Desktop/wget.bin".
There is no application installed for this file type
```

edit:
Solved. I should have not added ".bin" to the end of the file

---

### Post by anewguy on 2009-10-26
What you want to do is going to require programming of some sort, whether it be shell script programming, python, Java, C, C++, etc..  There are various tools to help along the way - some have been mentioned.  There are also tools to help you use the GTK libraries (GUI "stuff"), some of which build part of the code for you.  But no, there really isn't just a plug-and-go type of thing for this - you'll have to learn some programming but hey - why not?  It's not like you are at work and you really need to learn it fast - this is a hobby (from what it sounds like) for you, and you can work and learn at your own speed.  Nobody will judge you, and believe me, there is plenty of programming help available on the net - some in the Ubuntu forums, some in other sites.

My suggestion?  Pick one of the easier languages to learn, such as python or Java, then either get a book or just define what you want to do and start searching the net for help on getting started building a simple program and trying to grow it into what you want.  You'll have fun, you'll learn something new, and you'll get your project done the way you want in the process!

Dave :)

---

### Post by Marco A on 2009-10-26
.

---

### Post by ad_267 on 2009-10-26
Definitely don't try to build a GUI just yet, although using something like Zenity should be simple engouh.

Start with command line only programs to get started.

---

### Post by k3lt01 on 2009-10-26
> **nakama85 said:**
> I know that it seems like a dumb question but I figured I would ask and maybe someone would surprise me. I am looking to make a front end for something like wget (just to try it out). I know a couple already exist for wget I just want to use it as something to start with in order to learn the ropes.

ThanksGlade is a GTK GUI builder and is part of Gnome. It can be used on its own or as part of Anjuta which is also part of Gnome.

---

### Post by mivo on 2009-10-26
Can I throw in PureBasic? :) It is no free, but it does come with a GUI designer and compiles cross-platform (Win, Mac, Linux).

---

### Post by 3rdalbum on 2009-10-26
The programs I write are basically GUI frontends to various programs. I use Pythoncard; it's unmaintained and a bit buggy, and you need to know Python, but it has an interface designer and it's easy to whip up a program with it.

Python itself is easy to learn. It's a great language, I wish I could use it for everything.

Another option is Runtime Revolution. Not free and not cheap, but you can pick up a trial version from [www.runrev.com](www.runrev.com).  I'm not sure if you can run shell commands in it, but the language it uses is English-like and the package is based around its interface designer. An entire generation of Macintosh users learnt to program in Hypercard, and Runtime Revolution is basically Hypercard on steroids.  With a more expensive version of RunRev you can compile your programs for Macintosh and Windows too.

---

### Post by diesch on 2009-10-26
> **nakama85 said:**
> Thanks for the advice! I will definitely look into that. It just goes to show you how naive I am when it comes to programing. I truly thought that what I wanted to do was basic. 

Once you have some basic knowledge writing a simple GUI using Python isn't difficult. But making it really userfriendly and writing it in a way it's easy to extend and maintain  requires much more work and knowledge.

---

