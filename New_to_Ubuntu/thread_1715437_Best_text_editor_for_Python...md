---
title: "Best text editor for Python..?"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by .py on 2011-03-26
Hello ubuntuforums
Well, i'm new to Python and i'm looking for the best text editor, i used to work with IDLE, but it has some disadvantages, for example it doesn't show in which Line and Col i am...
So if you have programmed with python before, can you tell me which text editor is the best?
Thanks. :)

---

### Post by GWBouge on 2011-03-26
I'm probably in the minority, but I just use Gedit.

---

### Post by kellemes on 2011-03-27
[Geany]("http://www.geany.org/")

---

### Post by goldaryn on 2011-03-27
I used IDLE and Notepad++ on Windows

Maybe try scite, that's meant to be the thing Notepad++ was based on?

---

### Post by Old_Man_Unix on 2011-03-27
Traditionally,the "programmer's text editor" has been [FONT=Courier New]vim[/FONT] (or [FONT=Courier New]gvim[/FONT] ).  It includes scripts for many programming languages including Python.

There is definitely a learning curve with [FONT=Courier New]vim[/FONT]. 

If you insist on using [FONT=Courier New]gedit[/FONT], change the view to Scripts->Python.  Not as powerful as vim, but still much better than using the default view.

---

### Post by .py on 2011-03-27
> **Old_Man_Unix said:**
> Traditionally,the "programmer's text editor" has been [FONT=Courier New]vim[/FONT] (or [FONT=Courier New]gvim[/FONT] ).  It includes scripts for many programming languages including Python.

There is definitely a learning curve with [FONT=Courier New]vim[/FONT]. 

If you insist on using [FONT=Courier New]gedit[/FONT], change the view to Scripts->Python.  Not as powerful as vim, but still much better than using the default view.

Why choosing vim over Emacs..? :confused:

---

### Post by .py on 2011-03-27
> **kellemes said:**
> [Geany]("http://www.geany.org/")

i use Geany with Pascal and it simply ROX!! :)

---

### Post by Old_Man_Unix on 2011-03-28
> **.py said:**
> Why choosing vim over Emacs..? :confused:

This has been the big fight since before Linux even existed, going back to  UNIX days. 

Basically, it's one of those 'chocolate or vanilla' issues.   That's why I put "programmer's text editor" in quotes.

---

### Post by kellemes on 2011-03-28
> **.py said:**
> Why choosing vim over Emacs..? :confused:

This is one the old 'discussions', meaning.. not interesting anymore ;-)

Personally I still tend to use Vim (or Geany) but who cares what I use..
Just pick one of many fine multipurpose programmers-editors and stay with the one you feel most comfortable with.. it's all that counts.

---

### Post by ubudog on 2011-03-28
+1 for Gedit.  I've tried some others, but I always come back to Gedit.  Don't know why, but it's just nice.

---

### Post by cgroza on 2011-03-28
This is new and it might worth a look:
[https://sourceforge.net/projects/gecrit/](https://sourceforge.net/projects/gecrit/)

The author has debs under the "Files".

---

### Post by cgroza on 2011-03-28
> **Old_Man_Unix said:**
> Traditionally,the "programmer's text editor" has been [FONT=Courier New]vim[/FONT] (or [FONT=Courier New]gvim[/FONT] ).  It includes scripts for many programming languages including Python.

There is definitely a learning curve with [FONT=Courier New]vim[/FONT]. 

If you insist on using [FONT=Courier New]gedit[/FONT], change the view to Scripts->Python.  Not as powerful as vim, but still much better than using the default view.
Learning curve with vim? OK! What about being a keyboard Ninja with emacs?

---

### Post by .py on 2011-03-28
> **cgroza said:**
> Learning curve with vim? OK! What about being a keyboard Ninja with emacs?
Like ^_^

---

### Post by rosencrantz on 2011-03-29
This might sound wimpy considering the ferocious keyboard ninjas posting before me, but I am rather fond of full IDE's like eric, especially if there's major debugging going on. For shorter scripts I usually use Kate with ipython running in the terminal plugin, which is probably similar to GEdit.
Did anyone try Eclipse? I always found it terribly slow...

---

### Post by .py on 2011-03-29
> **rosencrantz said:**
> This might sound wimpy considering the ferocious keyboard ninjas posting before me, but I am rather fond of full IDE's like eric, especially if there's major debugging going on. For shorter scripts I usually use Kate with ipython running in the terminal plugin, which is probably similar to GEdit.
Did anyone try Eclipse? I always found it terribly slow...

Sorry but what is this ipython plug-in ?

---

### Post by rosencrantz on 2011-03-29
It's not a plugin, it's an enhanced interactive python shell and dead useful for running scripts and code snippets, among other things. It's available via apt-get and can be run in any terminal or terminal plugin (e.g. in gedit, kate, whatever...)

---

### Post by Learning Linux 2011 on 2011-03-29
Just out of curiosity, may I ask whether your school teaches Pascal on DOS/Windows or Linux?  What compiler do you use? 

 How far along are you in your studies?

---

### Post by leg on 2011-03-29
I like Geany. I have no idea how it is specifically for Python I use it for Java & C++ but it is good.

---

### Post by .py on 2011-03-29
> **Learning Linux 2011 said:**
> Just out of curiosity, may I ask whether your school teaches Pascal on DOS/Windows or Linux?  What compiler do you use? 

 How far along are you in your studies?

Well, i study computer science, first year. and i think me and Pascal get along pretty good. ^^
hmmm, they don't actually care what compiler you use, anyway labs PC's at university run Windows, and they use Turbo Pascal 7.0 .
but on my computer i use fpc (free pascal compiler) with geany.

---

### Post by cgroza on 2011-03-29
> **leg said:**
> I like Geany. I have no idea how it is specifically for Python I use it for Java & C++ but it is good.
Its even greater for python. So far, I did not found a replacement for it.

---

### Post by donkyhotay on 2011-03-29
> **GWBouge said:**
> I'm probably in the minority, but I just use Gedit.

Not as much of a minority as you may think, I also use gedit for coding in python. I find it simple to use and sufficient for my needs.

---

### Post by Fourcultures on 2011-05-03
There's a pretty full list of text editors for Python on the Python wiki:
[http://wiki.python.org/moin/PythonEditors](http://wiki.python.org/moin/PythonEditors)

I've used IDLE and SPE and prefer the latter. I'm new to Python so quite like the hand-holding you get with an IDE. There's a list of IDEs at [http://wiki.python.org/moin/IntegratedDevelopmentEnvironments](http://wiki.python.org/moin/IntegratedDevelopmentEnvironments) 
There's also a good discussion on IDEs for Python on[ StackOverflow]("http://stackoverflow.com/questions/81584/what-ide-to-use-for-python").
And a comment on the never-ending debate from a Python angle at [http://wiki.python.org/moin/EmacsVsVi](http://wiki.python.org/moin/EmacsVsVi)

Next, though, I'm going to try Geany.

---

### Post by oldfred on 2011-05-03
I like Geany, but find I have to change three settings to avoid space/tab issues.

There is a setting for editor in preferences to use 4 spaces in place of tabs. But if using projects you also have to set spaces there. Then it will still save a file with tabs unless you change the file save settings.

I was always pasting in sample code to understand it and test it but having line issues, due to tabs vs. spaces.

---

