---
title: "Best development tool/language for Ubuntu 9.10 Gnome"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by spiritofelric on 2010-01-27
Wondering what the recommended development tools are to create/manage window gui's on Ubuntu 9.10 (gnome desktop)?

I've heard of QT for KDE applications, or strict Java AWT for cross platform.

.

---

### Post by Temposs on 2010-01-27
GNOME's equivalent of Qt is Gtk(GNOME toolkit). Gtk is a library that has bindings in multiple languages like C/C++, Python, Vala, and Mono C#. The user interfaces for GTK are made with Glade. 

In terms of IDE's, you might try Anjuta for general GNOME development. 

If you decide to help with a Mono-based project(F-Spot, Banshee, Tomboy Notes), Monodevelop is a pretty good IDE. 

I personally like just using gedit with a bunch of developer-related plugins, which are numerous and make gedit a formidable IDE just by itself.

---

### Post by J V on 2010-01-27
Don't even think of using archaich languages like C/C++, use dynamically typed garbage collecting languages.

I would say python is the best, except it has no compiler (a real bitch for speed)

C# from mono is the next best thing, but I'm not sure v4 (dynamically typed) is ready yet...

gedit ftw btw ;P

---

### Post by Tahakki on 2010-01-27
I also just use gedit - there are lots of developer features built in. :)

If you use Python, you might want to look at Quickly too.

---

### Post by spiritofelric on 2010-02-26
> **Temposs said:**
> ...Gtk is a library that has bindings in multiple languages like C/C++, Python, Vala, and Mono C#...
> **J V said:**
> ...C# from mono is the next best thing, but I'm not sure v4 (dynamically typed) is ready yet...

Thank you so much for the info... you have no idea how much this helps.

I don't like the time it takes to write in C/C++.  Python is nice, but I'm not familiar with it.  Mono C#!?  I'm out of the loop... I thought that was a Microsoft language made to compete with Java.  I'll have to take a look into that.  I have some experience with it in .net.

Nice list of bindings for GTK:
[http://www.gtk.org/language-bindings.html](http://www.gtk.org/language-bindings.html)

Apparently you can use GTK in Windows, Mac, and GNU Linux/Unix... I'll have to look into how that actually works.

---

### Post by sandyd on 2010-02-26
p.s. if your designing gtk apps, you might wanna look at glade.
its a neat gtk interface designing tool.

---

### Post by grokwik on 2012-03-07
C++ archaic... The next Visual Studio version will be mainly oriented in C++ development :D
I don't say C++ is the best, but it's far from being archaic !!

---

### Post by Chiel92 on 2012-03-08
> **spiritofelric said:**
> Mono C#!?  I'm out of the loop... I thought that was a Microsoft language made to compete with Java.

Indeed, you're right. But the mono project has been started to enable i.a. C# programming under linux. The mono project covers the .NET framework, so all features brought by the use of a framework (.NET) will eventually be available for Mono.
The corrensponding IDE "MonoDevelop" is much like visual studio, so if you're familiar with Visual Studio, i'd recommend to give it a try.

---

### Post by oldos2er on 2012-03-08
Closed. Please don't bump old threads.

---

