---
title: "GUI programming for beginner"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by tagnu on 2011-07-22
Hi all, 

I've been using Ubuntu for sometime now. It is really good :)

Now, I would like to write small programs for my needs. Is there some simple tool to create gui programs (like a custom notepad or a simple calculator)?

Something like VB in Windows?

Thank you.

---

### Post by alphacrucis2 on 2011-07-22
> **tagnu said:**
> Hi all, 

I've been using Ubuntu for sometime now. It is really good :)

Now, I would like to write small programs for my needs. Is there some simple tool to create gui programs (like a custom notepad or a simple calculator)?

Something like VB in Windows?

Thank you.

Python might be a good start. It's cross platform so your programs will be easily ported to Windows and OSX.

---

### Post by marin123 on 2011-07-22
try monodevelop with GTK#.

you can find really good tutorials online. GTK# is gui for c# language and i think thats pretty easy language for beginners (even i learned to use it :D).

you can start here if youre interested in gtk#:

[http://monodevelop.com/Stetic_GUI_Designer](http://monodevelop.com/Stetic_GUI_Designer)

---

### Post by Nytram on 2011-07-22
I'd also suggest Monodevelop and C# it's easy to learn and there's plenty of help for that language on the web, which is useful for a beginner.

This tutorial shows how to build GUI's using Monodevelop:

[http://zetcode.com/tutorials/monowinformstutorial/]("http://zetcode.com/tutorials/monowinformstutorial/")

---

### Post by Nytram on 2011-07-22
> **alphacrucis2 said:**
> Python might be a good start. It's cross platform so your programs will be easily ported to Windows and OSX.

For your Python GUI program to work in Windows, it's necessary for your users to install Python and the graphical toolkit as well as your program. I don't think people many will do that.

---

### Post by anewguy on 2011-07-22
That's why I normally tell people to choose Java over it, since most Windows platforms already have Java.  Of course, this can also create the opposite effect.

To the OP:  I'm sorry to say I'm not familiar with C#, so I really can't give advice on that (I use C and GTK, but that would be difficult at best for a beginner).  What I can say is to stay enthusiastic and remember you don't have to stick with just one.  Try it, if you don't like it move on to another.  That's one of the beauties with Linux and open source - there are a lot of languages to select from, a lot of online tutorials for each, and plenty of sample code available.  Above all, don't get discouraged if you don't "get" something right away - just keep at it and you'll get there!

Best of luck!
Dave ;)

---

### Post by MG&amp;TL on 2011-07-22
C++ appears to have an infinite amount of linux-compatible libraries for GUI, however it can be a right pain to link them, whether you compile from command-line, or from an IDE.

My current favourite is Fast Light Tool Kit (FLTK), pronounced 'fulltick'.

---

### Post by anewguy on 2011-07-22
And as I mentioned for C and GTK, C or C++ probably is not a good place for a beginner to start at. ;)

---

### Post by MG&amp;TL on 2011-07-22
I completely agree, but I can't think of anything that would supply this simply. FLTK also has a (admittedly non-programming) attachment called Fluid, which I believe you can design your GUI system with. That was the main advantage in my mind, but I don't think you can get FLTK as anything other than C++ library.

---

### Post by snip3r8 on 2011-07-22
Qt creator is great for gui programming ,its C++ and very easy to use,in fact i think its the best IDE ive used for C++.That being said ,gambas is alot like VB.

---

### Post by cogier on 2011-07-22
Gambas is what you are looking for. It's in the Ubuntu Software Centre.

---

### Post by LemursDontExist on 2011-07-22
This is really two different questions - what programming language should you use, and what gui library. Windows comes with a default gui library written by Microsoft - which is what VB uses, but in Linux there's no clear default so you get to choose!

For the gui library, I think gtk is probably the most popular and widely supported - and it *is* the default library for the gnome environment.  You might also look into qt and wxWidgets which are popular.  

As for language, I don't think there's any basic based language that's popular on linux - but you're probably better off moving away from basic anyway - it's a bit of a programming dead end.  If you're looking for quick easy development, you definitely want a high level language like Python, C# or Ruby.  I'm personally a big proponent of Python.  Using C# in Linux is kind of strange since it was created by Microsoft for windows development, and is mostly popular among programmers who started on windows and don't want to learn a whole new language.  It's a workable option - but I wouldn't recommend it if you're not already invested.

---

### Post by tagnu on 2011-07-23
I'm very delighted to see so many replies. Thank you all :) 

My plan is to start with monodevelop and then move onto Python.

Here's the getting started tutorials for Gambas (might be useful for someone else):
[http://www.gambasdoc.org/help/tutorial](http://www.gambasdoc.org/help/tutorial)

> **anewguy said:**
>  What I can say is to stay enthusiastic and remember you don't have to stick with just one.  Try it, if you don't like it move on to another.  

I'll keep that in mind. Thank you.:)

Hopefully, I'll post my updates here 

Thank you again.

---

### Post by Pynalysis on 2011-10-04
When you start with Python you may like Tkinter.

---

### Post by mikechant on 2011-10-04
You could take a look at 'EasyGui' for Python. I had a quick go with this while teaching myself Python and it's certainly very easy to get started with (although it looks as if it might be a bit limited).

---

### Post by JremyDeaton on 2011-10-04
> **Nytram said:**
> For your Python GUI program to work in Windows, it's necessary for your users to install Python and the graphical toolkit as well as your program. I don't think people many will do that.

Orrrr.... Just extend you Python program with C++ "layers" like most people do. ;)

---

