---
title: "what does this error mean"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by ave2 on 2009-04-23
im trying to run a linux program called ivy generator, but get the following error- could someone explain what this means or even better how to fix it

error while loading shared libraries: libQtOpenGL.so.4: cannot open shared object file: No such file or directory

---

### Post by Roadbloc on 2009-04-23
i belive it may be something to do with OpenGL, which is the graphics. It may be requiring better graphics than what your machine or graphics card can provide. what is this program for/what does it do?

---

### Post by ave2 on 2009-04-23
the program generates 3d ivy as in the plant ivy in a 3d scene, so you can load in a house, and it will grow ivy up the wall..... 

[http://graphics.uni-konstanz.de/~luft/ivy_generator/](http://graphics.uni-konstanz.de/~luft/ivy_generator/)

I cant see how my computer wont handle it, I have a quad core, 4 gig ram, radeon 4850/ 512 gig running ubuntu 64 bit, and the program was last updated the beginning of 2007.... could it have something to do with the 64 bit distro I wonder?

---

### Post by PaulReaver on 2009-04-23
sorry for the stupid question 
have you installed your graphics card drivers

---

### Post by Roadbloc on 2009-04-23
hmmm... maybe. I think it may be to do with either Ubuntu not fully recognising your graphics card, your machine not just having a good enough graphics card or an incorrect installation. WHat is your graphics card and how did you install the program (eg. through add/remove or with the tarball provided on the site???)

---

### Post by ave2 on 2009-04-23
yeah I installed the latest graphic drivers, and programs like blender 3d are running smoothly at 600 000 polys after the install

some other people were having trouble getting this program to run, and this was one of the solutions proposed

Go to your terminal and type: 

sudo apt-get [SIZE=3]libqt4-dev[/SIZE]

cd /where the generator is/...

chmod +x IvyGenerator

but when I typed in the first command I got 

E: Invalid operation [SIZE=3]libqt4-dev[/SIZE]

---

### Post by Linux_Kid66 on 2009-04-23
i belive it may be something to do with OpenGL, which is the graphics. It may be requiring better graphics than what your machine or graphics card can provide. what is this program for/what does it do?
And,

---

### Post by Roadbloc on 2009-04-23
hmmm.... i am afraid i cannot think on what to do...
i'll have a think, but try seeing if you have installed it correctly. Your machine should be good enough to run it

---

### Post by freak42 on 2009-04-23
It doesn't (yet) have anything to do with your graphics card and also not directly with opengl..
what it says it's missing a library file to work (which is part of QT)
try

```
sudo apt-get install libqt4-opengl
```

hth

---

### Post by ave2 on 2009-04-23
> **freak42 said:**
> It doesn't (yet) have anything to do with your graphics card and also not directly with opengl..
what it says it's missing a library file to work (which is part of QT)
try

```
sudo apt-get install libqt4-opengl
```

hth

I ran the command, and got the following 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt4-opengl is already the newest version.
libqt4-opengl set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

hmmm so it looks like opengl is already the latest version

---

### Post by dawynn on 2009-04-23
Double check that you have a file named:
/usr/lib/libQtOpenGL.so.4
If you do, then perhaps your PATH isn't seeing /usr/lib?  (Check the PATH setting by running the command 'SET' from the command line)

If not, then you need to reinstall the libqt4-opengl package.  I just checked the Debian repositories, and it appears that this library has been in every libqt4-opengl package from stable all the way through experimental.

---

### Post by 3rdalbum on 2009-04-23
You say you're on 64-bit? Is the program 64-bit or 32-bit?

If it's 32-bit, you will need to install some 32-bit libraries; check out this thread on the Getlibs program which will help you with this: 

[http://ubuntuforums.org/showthread.php?t=474790]("http://ubuntuforums.org/showthread.php?t=474790")

---

### Post by ave2 on 2009-04-23
> **dawynn said:**
> Double check that you have a file named:
/usr/lib/libQtOpenGL.so.4
If you do, then perhaps your PATH isn't seeing /usr/lib?  (Check the PATH setting by running the command 'SET' from the command line)

If not, then you need to reinstall the libqt4-opengl package.  I just checked the Debian repositories, and it appears that this library has been in every libqt4-opengl package from stable all the way through experimental.

ok I checked, it appears that I do have that file already- how would I reinstall the package then

> **3rdalbum said:**
> You say you're on 64-bit? Is the program 64-bit or 32-bit?

If it's 32-bit, you will need to install some 32-bit libraries; check out this thread on the Getlibs program which will help you with this: 

[http://ubuntuforums.org/showthread.php?t=474790]("http://ubuntuforums.org/showthread.php?t=474790")

Ok I installed that .deb file at the link you supplied, and after I installed it, it said status: same version is already installed

is there anything else I need to do besides for installing the .deb file

---

### Post by 3rdalbum on 2009-04-23
> **ave2 said:**
> Ok I installed that .deb file at the link you supplied, and after I installed it, it said status: same version is already installed

Good, it's meant to say that.

> is there anything else I need to do besides for installing the .deb file

Re-read the thread - it tells you exactly how to use it. You need to run the program with getlibs, so getlibs can work out what libraries are needed and then install them. If that doesn't work, you can tell it the name of an Ubuntu package or a library and it will retrieve and install the 32-bit version of it.

---

### Post by ave2 on 2009-04-23
> **3rdalbum said:**
> Good, it's meant to say that.



Re-read the thread - it tells you exactly how to use it. You need to run the program with getlibs, so getlibs can work out what libraries are needed and then install them. If that doesn't work, you can tell it the name of an Ubuntu package or a library and it will retrieve and install the 32-bit version of it.

you are a genius!! it worked, thanks so much for the help  :guitar:

---

