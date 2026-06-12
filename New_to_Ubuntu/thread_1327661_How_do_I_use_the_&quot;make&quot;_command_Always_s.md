---
title: "How do I use the &quot;make&quot; command? Always shows up errors! Karmic"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by user333 on 2009-11-15
I have a problem with the make command. When I use it, it has two errors (that is all I understand, and the output is too long to post). I am trying to compile the widget factory, several drivers, and other other things like that. I always follow the tutorials on this step by step, but I still have this problem. Do I have a missing package? I this not the problem at all, or am I using it wrong? I usually use it like this: 

> make or 

> make installI **DO **use the ./configure command before I do this. I read that you will get errors if you don't use it. I will occasionally get an error from this too, but not often. I am doing the commands in the directory that the source files are in, and usually under sudo bash.

I know it is a very simple question, but I only recently started using Linux, and I am just learning the terminal.

---

### Post by coldReactive on 2009-11-15
Do the errors show that something isn't found?

If so, install the package (or similar package) that it mentions. Sometimes you gotta search hard. Wish make would auto-get the required packages to be honest. :|

Also, if you're making an i386 program on amd64, remember to install ia32-libs-dev

---

### Post by user333 on 2009-11-15
How do Install that package?

And the errors just say "ERROR 1" and "ERROR 2". Nothing else.

---

### Post by sisco311 on 2009-11-15
> **coldReactive said:**
> 
 Wish make would auto-get the required packages to be honest. :|


if the application is in the repos, you can:
```
sudo apt-get build-dep package-name
```

---

### Post by coldReactive on 2009-11-15
> **sisco311 said:**
> if the application is in the repos, you can:
```
sudo apt-get build-dep package-name
```

How about gnome2-globalmenu?

---

### Post by sisco311 on 2009-11-15
> **user333 said:**
> How do Install that package?

And the errors just say "ERROR 1" and "ERROR 2". Nothing else.

please post a link to the app and the exact error message.

---

### Post by user333 on 2009-11-15
well, this isn't in the repositories. Thats why I am trying to compile it. What about gnome2-globalmenu?

---

### Post by user333 on 2009-11-15
OK, just a second.

---

### Post by user333 on 2009-11-15
Here is the widget factory and I think the driver(I am having trouble with attachments). I am unable to post the error message. I don't want to publish my name. Here is just a few part of it:

make[2]: Nothing to be done for `all-am'.
make[2]: Nothing to be done for `all'.
And so on. For the widget factory, it doesn't show the error 1 and 2 message, but it doesn't work.

---

### Post by coldReactive on 2009-11-15
make clean

then make again, see if you get the error then.

---

### Post by user333 on 2009-11-15
I can't upload the driver, and I don't know where I got it. Anyway it is called "linuxwacom"

---

### Post by user333 on 2009-11-15
Make clean didn't show any errors...

---

### Post by sisco311 on 2009-11-15
TheWidgetFactory is in the universe repos:
```
sudo software-properties-gtk -e universe
sudo apt-get update
sudo apt-get install thewidgetfactory
```

globalmenu is available (for Hardy, Intrepid and Jaunty) from the ppa repo:  [https://launchpad.net/~globalmenu-team/+archive/ppa]("http://https://launchpad.net/~globalmenu-team/+archive/ppa")

compiling instructions: [http://code.google.com/p/gnome2-globalmenu/wiki/BuildFromSource]("http://code.google.com/p/gnome2-globalmenu/wiki/BuildFromSource")

edit:
biuld dependencies for globalmenu:
```
sudo apt-get install intltool  libgtk2.0-dev libwnck-dev libgnome-menu-dev libpanelappletmm-2.6-dev libnotify-dev
```

edit2: build dependency for linuxwacom:
```
sudo apt-get install xorg-dev
```

edit3: [thread=1038949]HOW TO: Install a LinuxWacom Kernel Driver for Tablet PC's[/thread]

---

### Post by user333 on 2009-11-15
Well, I don't know what to yet. The command didn't work. Thanks for your time :) I am getting tired, so I will quit checking this  thread today.

---

