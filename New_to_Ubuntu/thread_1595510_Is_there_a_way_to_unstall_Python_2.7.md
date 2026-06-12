---
title: "Is there a way to unstall Python 2.7?"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by dkjMusic on 2010-10-13
I installed 2.7 yesterday and am having problems with screenlets not running, etc.

Does anyone know a way of uninstalling 2.7 such that the system falls back to 2.6?

---

### Post by Melon Bread on 2010-10-17
*Bump* I would like to know as well

---

### Post by papibe on 2010-10-18
How did you install 2.7 ?

---

### Post by Yarui on 2010-10-18
> **papibe said:**
> How did you install 2.7 ?
Good point.  My system seems to be running 2.6 by default.  Did you install 2.7 on your own?  If not you could already be running 2.6.

(I'm not trying to suggest you aren't smart enough to know which version you are running.  Everyone makes mistakes and it can be helpful to ask these questions sooner rather than later.)

If you are, indeed, running 2.7 there seem to be entries for both 2.7 and 2.6 in the ubuntu software center.  Rolling back to 2.6 would probably be as simple as opening up the software center, uninstalling 2.7 and installing 2.6.

---

### Post by dkjMusic on 2010-10-18
I installed 2.7 on my own.

---

### Post by papibe on 2010-10-18
> I installed 2.7 on my own. 
I'm afraid we need more information to offer some advice. We need to know the method you used to install it. For example:

[INDENT][LIST]
[*]from a ppa, which one?
[*]from a .deb package, if so where did you get it?
[*]compiled from source, where did you get it?
[*]following instructions from a tutorial, which one?
[/LIST]
[/INDENT]

Regards.

---

### Post by Melon Bread on 2010-10-18
(Running 10.10 x64)
I would guess from source from the python homepage, at least thats how I did it.
[http://www.python.org/download/](http://www.python.org/download/)

I used this one:
[http://www.python.org/ftp/python/2.7/Python-2.7.tar.bz2](http://www.python.org/ftp/python/2.7/Python-2.7.tar.bz2)

Just did a basic

[I]./configure
sudo make
sudo make install[/I]

Note Python 2.6.5 is still installed yet nothing works (it seems like its trying to use 2.7)


It sounds like the OP is in the same boat as myself

---

### Post by papibe on 2010-10-18
I have downloaded the package, read the docs, and went to the python wiki site. It does not look promising. It seems there's no actual uninstall process/tool yet (but it's in the making: [read here]("http://wiki.python.org/moin/Distutils/Proposals/UninstallCommand")).

Also I've learned that several versions can coexist together. You just need to point to the one you want to use. In my case:
```
$ ls -l /usr/bin/python*
lrwxrwxrwx 1 root root       9 2010-06-27 12:56 /usr/bin/python -> python2.6
lrwxrwxrwx 1 root root       9 2010-06-27 12:56 /usr/bin/python2 -> python2.6
-rwxr-xr-x 1 root root 2288240 2010-04-16 09:06 /usr/bin/python2.6

```
The actual "python" command is a symbolic link to python2.6. Check how python is set in your system. If you are in a similar situation in which python is just a link, then you could do this:

```
$ sudo rm /usr/bin/python /usr/bin/python2
$ sudo ln -s /usr/bin/python2.6 /usr/bin/python
$ sudo ln -s /usr/bin/python2.6 /usr/bin/python2
```
This way any reference to "python" will go the 2.6 version.

Good Luck!

---

### Post by Melon Bread on 2010-10-18
@papibe: Thank you, I went ahead and got help on IRC, but your way works just as well. Thanks for posting the solution :KS

---

### Post by papibe on 2010-10-18
You're very welcome. If you finally learned how to uninstall it, or got a better method that the link trick, please post it here. That way, other users read benefit from it.

Regards.

---

### Post by croquet on 2010-11-15
Dear **Melon Bread**, could you be as kind as to post how did you manage to uninstall Python2.7?
I installed it following exactly the same steps as you but even after following **papibe** suggestion (thanks man!) when I type python on the terminal it launches python2.7 

Some users of LinuxMint are having an *OAFIID:GNOME_mintMenu*,due to the installation of Python2.7 ([here](http://forums.linuxmint.com/viewtopic.php?f=90&t=13951))
The system uses Python2.6 by default and it seems to be an incompatibility with newer Python versions.

I am one of those users and after reading this post I am sure it is due to Python 2.7 and (maybe) getting rid of it will fix that issue.

Thank you very much in advance!

---

### Post by croquet on 2010-11-17
I fixed the issue without having to uninstall Python2.7

The problem was that Python2.6 (default system one) was installed in */usr/bin/* and despite the symbolic links were properly pointing to it, the python bash command was not.

Python2.7 was installed at */usr/**local**/bin* and the bash command python was pointing to this one.

Checking the path I found this:

```
caterina@Pies ~ $ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

As you can see, first it looks in */usr/local/bin* (where Python2.7 is installed) and then it looks in */usr/bin* (where Python2.6 is installed)

So the solution was to do the following:

```
mv /usr/local/bin/python /usr/local/python27link
```

Now, If I type *python* in a terminal it launches Python2.6 whereas if I type *python27link* it launches Python2.7 
Of course, after fixing this mess I could get mintMenu back yuju!!

Maybe there's a more elegant way to solve this, for instance changing the reference of python bash variable, but I don't know how to do it and none of the suggestions given worked for me.
Hope it does too for someone stuck in the same situation as I was.

---

### Post by sisco311 on 2010-11-17
On a side note, python2.7 is in the Maverick repositories. 

And if you have to compile a package from source, you should always read the README and/or INSTALL files.

From the python README:
```
Installing multiple versions
----------------------------

On Unix and Mac systems if you intend to install multiple versions of Python
using the same installation prefix (--prefix argument to the configure
script) you must take care that your primary python executable is not
overwritten by the installation of a different version.  All files and
directories installed using "make altinstall" contain the major and minor
version and can thus live side-by-side.  "make install" also creates
${prefix}/bin/python which refers to ${prefix}/bin/pythonX.Y.  If you intend
to install multiple versions using the same prefix you must decide which
version (if any) is your "primary" version.  Install that version using
"make install".  Install all other versions using "make altinstall".

For example, if you want to install Python 2.5, 2.6 and 3.0 with 2.6 being
the primary version, you would execute "make install" in your 2.6 build
directory and "**make altinstall**" in the others.

```

---

