---
title: "Text Editors"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by dondiego2 on 2010-02-24
I have been using Ubuntu since December and I love it.  But I am a little confused about text editors.  I was messing around with Python programming and I was using gedit and I like the way it works.  It's kind of like notepad for Windows as far as I can see but a little more powerful.

I then was doing a tutorial the other day and they recommended doing short Python programs in Vim, which you can run right from the Python editor.  I was following examples and opened up a Vim window and could not figure out how to even use it.  I stumbled across some commands to get started and had to google to figure out how to end it.

I read in the forums that a lot of people swear by Vim.  Why?  What makes it better then gedit that works more like a simple word processor?  Is it more powerful and in what way?  It seems like it took me back to my terminal days when I was learning Fortran programming on punch cards :-)

Am I missing something?

---

### Post by ibuclaw on 2010-02-24
> **dondiego2 said:**
> I have been using Ubuntu since December and I love it.  But I am a little confused about text editors.  I was messing around with Python programming and I was using gedit and I like the way it works.  It's kind of like notepad for Windows as far as I can see but a little more powerful.

I then was doing a tutorial the other day and they recommended doing short Python programs in Vim, which you can run right from the Python editor.  I was following examples and opened up a Vim window and could not figure out how to even use it.  I stumbled across some commands to get started and had to google to figure out how to end it.

I read in the forums that a lot of people swear by Vim.  Why?  What makes it better then gedit that works more like a simple word processor?  Is it more powerful and in what way?  It seems like it took me back to my terminal days when I was learning Fortran programming on punch cards :-)

Am I missing something?

Vim is awesome. :)

It starts as a minimal text editor, but you can build it to be your own IDE over time. It is modal - meaning that there are more than just an "Insert" mode that you find on any other editor.

I'd recommend the full package (as the one installed by default is the minimal vi).
```
sudo apt-get install vim
```
and get started with it by running:
```
vim-tutor
```
And as for GUI, have a look at gvim:
```
sudo apt-get install vim-gnome
```

Gedit is just as extensible too, though, with the gedit-plugins package.
Another of my favourite IDEs is geany too.

Regards
Iain

---

### Post by mcduck on 2010-02-24
command-line based editors tn to have lots of features that are missing from graphical editors (adding all the features and editing tools to a graphical editor would make the user interface quite a mess), and are easily used with keyboard only. But that doesn't really mean that you *should* use one if you feel that Gedit has everything you need.

Besides, Gedit is extensible via plugins, so you can turn it from a fairly-simple text editor into insanely powerful development environment, if you want to..

While you may be able to run Vim inside Python, you are also able to run Python (or Vim) inside Gedit... :D

---

### Post by dondiego2 on 2010-02-24
Thanks for the answers so far.  I was confused when Vim opened up.  I did not even know how to type in text.  I stumbled across a key combo for inserting text I guess.  Then it took me a while to figure out the ZZ to exit command.

I guess there is a learning curve as with most things I am finding out in Linux as i come from Windows.  But that's OK, I like learning new things.

---

### Post by Tibuda on 2010-02-24
> **dondiego2 said:**
> Thanks for the answers so far.  I was confused when Vim opened up.  I did not even know how to type in text.  I stumbled across a key combo for inserting text I guess.  Then it took me a while to figure out the ZZ to exit command.

I guess there is a learning curve as with most things I am finding out in Linux as i come from Windows.  But that's OK, I like learning new things.

I use GVim myself, and find it amazing, but you could use any text editor you are confortable with.

---

### Post by n0dix on 2010-02-24
> **dondiego2 said:**
> Thanks for the answers so far.  I was confused when Vim opened up.  I did not even know how to type in text.  I stumbled across a key combo for inserting text I guess.  Then it took me a while to figure out the ZZ to exit command.

I guess there is a learning curve as with most things I am finding out in Linux as i come from Windows.  But that's OK, I like learning new things.

At the beginning is a little slow to get the features and shortcuts, etc, but is  great for programming. It's so minimalistic  ;) ...

---

### Post by sukamusiru on 2010-02-24
> **dondiego2 said:**
> Thanks for the answers so far.  I was confused when Vim opened up.  I did not even know how to type in text.  I stumbled across a key combo for inserting text I guess.  Then it took me a while to figure out the ZZ to exit command.

I guess there is a learning curve as with most things I am finding out in Linux as i come from Windows.  But that's OK, I like learning new things.

You can find any number of handy cheat sheets (ex: [http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html)) to get you started. While the learning curve may be a bit of a hump, it can be a great tool. One of the focuses of Vi/Vim is to give complete control to the keyboard so that your fingers are almost always somewhere near home row.

By the way,

i enters insert mode (what you type goes into the doc)
esc leaves insert mode (what you type goes to Vim as a command)

ZZ saves and exits
q! exits without saving
q exits or warns you that changes have been made

---

### Post by dondiego2 on 2010-02-24
> **sukamusiru said:**
> You can find any number of handy cheat sheets (ex: [http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html)) to get you started. While the learning curve may be a bit of a hump, it can be a great tool. One of the focuses of Vi/Vim is to give complete control to the keyboard so that your fingers are almost always somewhere near home row.

By the way,

i enters insert mode (what you type goes into the doc)
esc leaves insert mode (what you type goes to Vim as a command)

ZZ saves and exits
q! exits without saving
q exits or warns you that changes have been made


Thanks!  With that little lesson I'm already a lot more comfortable.

---

### Post by SoFl W on 2010-02-24
The Vim commands cheat sheet:
[http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html)

Once you get used to it, it is great to use and you will easily move through all the commands.  

You can also try "nano <FILENAME>" (from the command line).  Nano is like an old ascii text editor from the DOS days.

---

