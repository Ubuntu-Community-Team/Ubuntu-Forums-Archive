---
title: "a basic question about ubuntu architecture"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by Nebelhom on 2010-12-20
Hi guys,

after a long time of letting my frustration come down (about 1 year I think) I am taking another shot at installing pyaudiere on ubuntu from source.

Now the website [(Click here to get there)]("http://pyaudiere.org/") is incredibly hazy in its HowTo for that (to me anyway)

And here is the question:
(This is from the website)
> "The deb package depends on libaudiere-1.9.4, which is available in both Debian and Ubuntu package repositories. The Windows installers have no dependencies (except numpy if you want to play arrays, of course). **To build from source, extract into the /audiere/bindings folder in the Audiere source distribution** right beside the included Python bindings folder and issue the standard 'python setup.py build' command."

Now where do I find the /audiere/bindings folder in the Audiere source distribution?

I realise that this is potentially a very basic question, but I simply don't get it.

---

### Post by oldfred on 2010-12-20
So not know for sure but have you installed from synaptic the  libaudiere packages? That may set up those directories.

---

### Post by Nebelhom on 2010-12-20
Hi,

thanks for your answer. I installed libaudiere via synaptic. when searching for an audiere folder, I can only find a libaudiere folder not an audiere one.

This annoys me, because I have used this library on Windows and installed it with an installer and now I can't use it on my preferred operating system...

thanks for your help. it is very appreciated.

---

### Post by Nebelhom on 2010-12-20
Bump.

Noone else? I'm open for any suggestions.

---

### Post by oldfred on 2010-12-20
A .deb does not require building from source. I think those are two different sets of instructions. 

I have only installed one or two apps from .debs but I just double clicked on them. Not sure if I installed something that helps that or not, as I did that a long time ago.

---

### Post by Nebelhom on 2010-12-20
yea, unfortunately, I cannot use that .deb because xubuntu lucid has python2.6 installed as standard and that .deb is for python2.5. It throws an exception when I want to use it. So it seems that I am stuck at trying to install from source, but the standard ways of doing it do not work :(

---

### Post by oldfred on 2010-12-20
I do not understand error like you are having. There have been several other posts with similar issues, but 2.6 was supposed to be backward compatible with 2.5. Sometimes newer version like 2.6 based might check that version is not older as perhaps newer features are used. 

Also now python 3 is not compatible with the 2.x series.

Ubuntu requires 2.6, you can also install 2.5 ( I think) but then you have issues getting the software to always use the 2.6 version. 

Not sure if there is a way to get the software to think it is 2.5 even if it is 2.6?

---

### Post by sandyd on 2010-12-20
> **Nebelhom said:**
> yea, unfortunately, I cannot use that .deb because xubuntu lucid has python2.6 installed as standard and that .deb is for python2.5. It throws an exception when I want to use it. So it seems that I am stuck at trying to install from source, but the standard ways of doing it do not work :(
installing from source will **not **make a difference when using python-based programs. If it doesn't run with the debs (after a --force all i mean) it won't run if you build it from source. The program will have to be rewritten with the correct functions for python 2.6.

---

### Post by Nebelhom on 2010-12-21
hmmm..., that is strange, since they updated the windows versions to fit python2.6 and 2.7...

Thanks for the tip. could you maybe elaborate on the --force all part (as in what exactly I would have to do to try that)? I'm one of those nothing knowing windows converts and no matter how often I use the command line, the commands seem to slip my mind again and again :?

Thanks mate.

---

### Post by jtarin on 2010-12-21
In the past I have been able to get somethings to run by symlinking to the installed application (python2.6) and renaming the symlink to an older version number (python2.5). This is no guarantee but its worth a shot. Make sure your path to the symlink is where the program will normally look for it....usually in the same directory as the original.

---

### Post by Nebelhom on 2010-12-21
Hi guys,

thanks for all your input. I have done it now via a slightly different way.

I installed python2.5 alongside python2.6 using the instructions on the python site ([http://www.python.org/download/releases/2.5.5/](http://www.python.org/download/releases/2.5.5/)) and posts from this page ([http://ubuntuforums.org/showthread.php?t=1468661](http://ubuntuforums.org/showthread.php?t=1468661)).

The only alteration to the installation on the python homepage, was to use the command

```
make altinstall
```

instead of

```
make install
```

This allows me now to run both python versions without the installation getting confused over which version to use.

This now poses a different problem, but that is unrelated, so that I will open a different thread for that.

Thanks again folks

---

