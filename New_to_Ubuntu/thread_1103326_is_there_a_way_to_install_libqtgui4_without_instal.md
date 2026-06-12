---
title: "is there a way to install libqtgui4 without installing all dependencies?"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by gandaran on 2009-03-22
is it possible to just install libqtgui4 without the dependencies?

---

### Post by llamabr on 2009-03-22
you could download the .deb and use dpkg -i

why would you not want the dependencies?

---

### Post by gandaran on 2009-03-22
> **llamabr said:**
> you could download the .deb and use dpkg -i

why would you not want the dependencies?
I don't like qt libs polluting my gnome, but this one I need to run a qt application I can't do without and the dozen or so dependencies it installs are useless just taking up disk space.
thanks, I'll give it a try using dpkg -i.

---

### Post by snova on 2009-03-22
> **gandaran said:**
> is it possible to just install libqtgui4 without the dependencies?

These?

```
Depends: libaudio2, libc6 (>= 2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.12.0), libice6 (>= 1:1.0.0), libjpeg62, libmng1 (>= 1.0.3-1), libpng12-0 (>= 1.2.13-4), libqtcore4 (= 4.4.3-0ubuntu1), libsm6, libstdc++6 (>= 4.1.1), libtiff4, libx11-6, libxext6, libxi6 (>= 2:1.1.3-1ubuntu1), libxrandr2, libxrender1, zlib1g (>= 1:1.1.4), fontconfig
```

Almost every one of those is absolutely necessary. There is a way to force installation of a package without installing dependencies, but if you did, libQtGui would not work. Period.

Of those, a few of them might be "optional", but they'll be the image codecs. And not only will it probably not work anyway, but they are small besides and won't save much space.

> **llamabr said:**
> you could download the .deb and use dpkg -i

dpkg will complain about missing dependencies if you try that. ;)

---

### Post by Bachstelze on 2009-03-22
> **gandaran said:**
> is it possible to just install libqtgui4 without the dependencies?

No. Dependencies are here for a reason.

---

### Post by jtb_90 on 2009-03-22
N00b question but hey I'm a Linux n00b..

What are dependencies? :S

---

### Post by llamabr on 2009-03-22
Dependencies are all the other applications and libraries required to run the program.

I agree.  You could use dpkg to force the install, but it's not going to run anyway without the libraries.

I'm still not sure why you'd want to do that.  Maybe there's another way to accomplish what you want?

---

### Post by anewguy on 2009-03-22
You like food, right?  Kind of a dependency for human life.  So is breathing, a beating heart, etc..  They are needed to live.  Software dependencies are no different - a piece of software, in this case your libqtgui4, was built knowing that these other tools would be available for it to live.

Sometimes you can go through apt-get and install something without it directly complaining on dependencies until it gets to the configure or make - then it complains.  If a package makes it through apt-get without forcing you to get it's dependencies, it will eventually fail.  In that case you can do the following to get the dependencies:

sudo apt-get build-dep <package-name>

I've had to do that more than a few times in the past, but lately everything seems to behave better - I don't know if it's a change to what ever underlies apt-get or what, but I just don't seem to come up with missing dependencies anymore except for some 3rd party packages.

Dave :)

---

### Post by jtb_90 on 2009-03-22
Oh so are dependencies like software engines? Or is that me getting confused?

---

### Post by JohnLM_the_Ghost on 2009-03-22
> **gandaran said:**
> is it possible to just install libqtgui4 without the dependencies?

Compile from source (although it will still require most of those)... other than that, no you can't!

You can however skip installing recommendations! (those are not mandatory)


> **jtb_90 said:**
> Oh so are dependencies like software engines? Or is that me getting confused?
Well this depends on package...
Linux (and other *nix) based operating system's programs work quite different compared to... let's say Windows!
On *nix, you have a bunch of little pieces of software working together. So virtually every little program requires few other to help do it's work. It's like a harmony! (At least in theory)
So those programs (and also some other stuff) are dependencies for that particular program. Without them it won't work.

In Windows however most programs comes with it's dependencies included. (which is a waste of space and makes system less modular)

Hope you understand what I wrote... cause I quite don't! :D

---

### Post by gandaran on 2009-03-23
> **snova said:**
> These?

```
Depends: libaudio2, libc6 (>= 2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.12.0), libice6 (>= 1:1.0.0), libjpeg62, libmng1 (>= 1.0.3-1), libpng12-0 (>= 1.2.13-4), libqtcore4 (= 4.4.3-0ubuntu1), libsm6, libstdc++6 (>= 4.1.1), libtiff4, libx11-6, libxext6, libxi6 (>= 2:1.1.3-1ubuntu1), libxrandr2, libxrender1, zlib1g (>= 1:1.1.4), fontconfig
```

Almost every one of those is absolutely necessary. There is a way to force installation of a package without installing dependencies, but if you did, libQtGui would not work. Period.

Of those, a few of them might be "optional", but they'll be the image codecs. And not only will it probably not work anyway, but they are small besides and won't save much space.



dpkg will complain about missing dependencies if you try that. ;)

after trying a couple times I succeeded removing almost all dependencies with synaptic without removing libqtgui4 too but theres still one I can't remove and yes the application stills runs fine it only needs libqtgui4 to run. 
can you show me the way to force install a package without installing dependencies?
thanks.

---

### Post by JohnLM_the_Ghost on 2009-03-23
Only package (and it's dependencies) that can be removed safely is **qt4-qtconfig** (which is a recommended package of **libqtgui4**)
try running
```
sudo apt-get remove qt4-qtconfig libqt4-qt3support libqt4-designer libqt4-sql
```
Be aware that I didn't take into account any other QT apps might be using these.
apt-get should warn about packages that won't work anymore, so read those thoroughly.

---

