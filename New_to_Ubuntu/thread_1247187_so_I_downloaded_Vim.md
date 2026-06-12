---
title: "so I downloaded Vim"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by filifunk on 2009-08-22
how do you run the program?  I don't see it under applications.  When I go to the terminal I can type "vim" and it looks like I might be in it, but it looks nothing like the screenshot on synaptic.  

Is that how you run something that you've just installed?  Just type it in?

---

### Post by BackwardsDown on 2009-08-22
Whahaha, the screenshot is a screenshot of Synaptic showing vim :lolflag:.

The commandline thing is indeed Vim.

---

### Post by filifunk on 2009-08-22
so I guess I don't understand how a text editor works. 

When I get into the terminal, I type python and start doing some python and it works.

example:

print "hello world" will actually print "hello world"


but when I type in an editor it doesn't work.  Do I have to let it know that I'm using python?

---

### Post by BackwardsDown on 2009-08-22
Vim is not a "normal" editor. It has a very steep learning curve. If you only want to edit files and not bother with advanced stuff use the editor nano. You can start it the same way as vim. Its a simpler editor with less features.

If you really want to learn Vim, find a tutorial (for example this: [http://heather.cs.ucdavis.edu/~matloff/UnixAndC/Editors/ViIntro.html](http://heather.cs.ucdavis.edu/~matloff/UnixAndC/Editors/ViIntro.html))

---

### Post by ceramicm on 2009-08-22
There are at least three ways you can run programs in Ubuntu.

1. Most graphical programs can be found in the Applications, Places, System menu at the top left of the screen.

2. Applications can also be launched by pressing <Alt>F2 then typing in the name of the program and pressing <Enter>.

3. Non-graphical (text-only) programs such as Vim can only be run in something called the terminal. The terminal can be opened by clicking Applications->Terminal in Ubuntu.

If your screenshot looks like the attached file then yes, that is the VIM text editor.

As said before, VIM is an advanced text editor. If you would like to edit files in a graphical text editor, I would suggest gedit. It should be installed by default. It works similarly to Windows Notepad.

Edit:
In answer to your python question, most basic text editors will not execute the code you write as you write it. If you want to execute some python code, first save your file as something like "foo.py" then run "python foo.py" in a terminal to execute it.

---

### Post by Paddy Landau on 2009-08-22
You're using Ubuntu, right? Which means you're using the GUI?

Try using the built-in gedit.
Applications > Accessories > Text Editor

---

### Post by filifunk on 2009-08-22
> **ceramicm said:**
> 

Edit:
In answer to your python question, most basic text editors will not execute the code you write as you write it. If you want to execute some python code, first save your file as something like "foo.py" then run "python foo.py" in a terminal to execute it.

Ok, I think I'm understanding it.  I've used gedit to make "helloworld.py", now how do i execute it in terminal?

---

### Post by j.bell730 on 2009-08-22
> **filifunk said:**
> Ok, I think I'm understanding it.  I've used gedit to make "helloworld.py", now how do i execute it in terminal?

Type
```
python path/to/script.py
```

---

### Post by filifunk on 2009-08-22
IT WORKS! HELLO WORLD! haha thanks everyone.  Daft Punk rules btw.

---

### Post by dlmarti on 2009-08-22
> **ceramicm said:**
>  As said before, VIM is an advanced text editor. 

Advanced? since when? VIM is basically VI written back in 1976 for editing files over a 300 baud modem.

I would hardly call that advanced, and I certainly wouldn't recommend it for a person starting out (or even someone experienced).

The ONLY value of VI/VIM is the experience and skill of the user.  If someone doesn't already have the skill to use VI it is hardly rewarding for him/her to learn.

For simple editing use pico/nano or one of the easy graphical editors.  For more advanced stuff there are hundreds of better solutions than VI.

---

### Post by BackwardsDown on 2009-08-22
> Advanced? since when? VIM is basically VI written back in 1976 for editing files over a 300 baud modem.

With advanced I mean the amounts of functionality it offers. I have not been able to think of an text editor feature that is not possible with Vi/Vim (ok, it does not respond to your mouse :)). I call that advanced.

---

### Post by dlmarti on 2009-08-22
> **BackwardsDown said:**
> With advanced I mean the amounts of functionality it offers. I have not been able to think of an text editor feature that is not possible with Vi/Vim (ok, it does not respond to your mouse :)). I call that advanced.

Column copy?
Search and replace across multiple buffers?
Editing a ftp/scp source?
auto-completion based on language?
built-in lint?
how about looking up function definitions?
or maybe looking up the scope and original definition of a define/function?

Bottom line is, if you really want a productivity booster, vim is NOT it.

---

### Post by NathanLT on 2009-08-22
Personally I find that I can edit text much more quickly in Vim than I can in a graphical text editor such as gedit. Being able to do stuff like delete, copy and paste lines, move around quickly, and access the commandline without switching programs, all without having to move from the keyboard to the mouse and back again, makes my life a lot easier. None of that stuff is anywhere near as advanced as the features listed by dlmarti, but it's what I spend 99% of my time doing. It's being able to do the simple stuff quickly that really makes a difference to my productivity. 

(BTW, search and replace across multiple buffers is possible with the :bufdo command; Vim 7 allows the editing of ftp, scp, http, dav, and rcp sources, among others; <Ctrl-X> <Ctrl-O> will get you autocompletion in C, C++, CSS, HTML, JavaScript, PHP, Python, Ruby, SQL or XML depending on the file you're editing; column copy is a breeze in visual mode (just hit <Ctrl-V>); function definitions are simple with tags, and Vim plays nicely with ctags and all the other *tags out there; plugins are available for lint.)

And remember, Vim is only a text editor, not an IDE!

---

### Post by BackwardsDown on 2009-08-23
> **dlmarti said:**
> Column copy?
Search and replace across multiple buffers?
Editing a ftp/scp source?
auto-completion based on language?
built-in lint?
how about looking up function definitions?
or maybe looking up the scope and original definition of a define/function?

Bottom line is, if you really want a productivity booster, vim is NOT it.

A lot of things are implented in Vim. Like code completion, scope of function, and even spell checking.

Check this out for example: [http://linuxhelp.blogspot.com/2006/09/visual-walk-through-of-couple-of-new.html](http://linuxhelp.blogspot.com/2006/09/visual-walk-through-of-couple-of-new.html)

---

### Post by 3rdalbum on 2009-08-23
What about vim-gnome? Apparently, it's Vim with a Gnome 2 interface.

---

### Post by Joeb454 on 2009-08-23
> **3rdalbum said:**
> What about vim-gnome? Apparently, it's Vim with a Gnome 2 interface.

Or gvim? Though they could quite possibly the same thing

---

