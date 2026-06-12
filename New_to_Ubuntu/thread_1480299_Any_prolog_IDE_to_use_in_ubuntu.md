---
title: "Any prolog IDE to use in ubuntu?"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by legolas_w on 2010-05-11
Hi

I will be at university from august and I will need to develop Prolog applications. Is there any IDE for Prolog which works in ubuntu?


thanks.

---

### Post by legolas_w on 2010-05-12
Hi,

Any comment on this?

thanks

---

### Post by molar on 2010-05-12
maybe you'll find something in here?
[http://stackoverflow.com/questions/282968/whats-a-good-prolog-ide-for-linux](http://stackoverflow.com/questions/282968/whats-a-good-prolog-ide-for-linux)

---

### Post by WRDN on 2010-05-12
I've recently finished a Prolog related assessed coursework at Hull University (English Parser). I used SWI-Prolog, though I have also used GNU Prolog. They are both in the repositories, with the package names, "swi-prolog" and "gprolog" respectively. To install both:

```
sudo apt-get install swi-prolog gprolog
```

---

### Post by cap10Ibraim on 2010-05-12
I use swi-porlog from the terminal , but in windows it has a UI 
missing something ?

---

### Post by jecaestevez on 2010-06-18
you must download a [java prolog editor]("http://www.trix.homepage.t-online.de/JPrologEditor/JPrologEditor.jar")

---

### Post by Patrick.Rypalla on 2010-06-21
You find only an old version of SWI-Prolog in the Universe repository. We had some trouble with it, so I set up an launchpad repository. 
Maybe you want to install the newer Version, so you can find it here:
[https://launchpad.net/~patrick-rypalla](https://launchpad.net/~patrick-rypalla)

There is a bug in the current released versions which caused at compiling a rpath error but its already fixed in the official swi-prolog git repository.
Therefor I suggest to Install the 5.11 (development version) if you want to install a newer version then the one in the Ubuntu repository.

And if you looking for an Editor, there is an build in ide in swi-prolog. Just start swi-prolog with "swipl" after you installed it and typ "emacs." in the swi-prolog terminal

---

### Post by rsmitty on 2010-06-21
I had to do a Prolog project for a class and did not find a GUI similar to the Windows GUI. Although a buddy of mine seemed to have problems with the Windows GUI anyways. I did, however, find it useful to enable the Prolog highlighting in GEdit. That helped with the development process quite a bit.

---

### Post by Patrick.Rypalla on 2010-06-21
I forgot to say, there is a good Eclipse Plugin:
[http://sewiki.iai.uni-bonn.de/research/pdt/start](http://sewiki.iai.uni-bonn.de/research/pdt/start)
but unfortunately there are some problems with the next release. So the current release candidate r5 (which is to suggest) doest not work with the new swi-prolog versions. the best swi prolog version for the current release is 5.8.3 which can also be found on my launchpad. 
The next release will be working with swi-prolog 5.11 which brings some advantages along[]("http://dict.tu-chemnitz.de/english-german/unfortunately.html")

---

### Post by Metal Fan on 2010-09-04
Hi!

Prolog Development Tools (ProDT) is a Prolog Integrated Development Environment (IDE) aiming to be as rich in functionality as the Eclipse's java IDE, giving the developer a single environment where it can control the development of a Prolog project from code edition, test execution, etc...

This project stands on top of Eclipse's projects to take advantage of its already existent features and its extensibility and works on any environment Eclipse works including windows, linux and mac OSX.

It support as underlying interpreters: SWI-prolog, XSB prolog, B-prolog

The site has more information about the project including installation and features list: [http://prodevtools.sourceforge.net/](http://prodevtools.sourceforge.net/)

Hope you can find it useful!!! :)

---

