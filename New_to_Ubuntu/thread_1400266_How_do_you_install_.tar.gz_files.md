---
title: "How do you install .tar.gz files?"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Nicolas.Perrault on 2010-02-06
Okay, I've tried to install mupen64plus v1.99, but I can't find a way to install it. I've extracted the files and found the install file. When I double click it, the following box appears: 

[SIZE="5"]Do you want to run install.sh or display its content?[/SIZE]

Available options:

1) Run in Terminal
2) Display
3) Cancel
4) Run

Run and Run in Terminal do absolutely nothing, while Display displays what seems to be the source of the installer.

Any help?

Thanks!

---

### Post by mushwars on 2010-02-06
```
mkdir ~/opt
cp /path/to/.tar.gz ~/opt
cd ~/opt 
tar xvzf your.tar.gz
cd yourfolder
sh ./configure
make
sudo make install
```

---

### Post by Linux000 on 2010-02-06
so, the file is a .tar.gz , if it is, then extract it into a folder in say, home. when thats done, run terminal and type
```
cd (where ever you extracted it to)
```
then
```
./configure
```
this will either say file not found or print out a bunch of text, either way its fine, next
```
make
```
finally
```
sudo make install
```
that should be it.

---

### Post by Paqman on 2010-02-06
> **Nicolas.Perrault said:**
> Okay, I've tried to install mupen64plus v1.99, but I can't find a way to install it.

Mupen64plus is available in the Ubuntu repositories, you just need to enable the Universe repo. Go to System > Admin > Software sources and check the box for Universe, then let it reload when it prompts. After that you'll be able to get your software from Ubuntu Software Centre or Synaptic.

Generally installing from tar.gz should only be used as a last resort. The package manager is always the first and best place to get software from.

---

### Post by Nicolas.Perrault on 2010-02-06
@paqman: Well the box is already checked, but it's true that mupen64plus is available through Ubuntu Software center, but that's v1.5. I'm looking for v1.99.

@linux000: I have no idea. First, I'm restricted access to home. Second, I try to use your first code but it doesn't find the directory.

Thanks for any ideas! 

By the way, why should I avoid installing through .tar.gz? ;)

---

### Post by mushwars on 2010-02-06
> **Nicolas.Perrault said:**
> By the way, why should I avoid installing through .tar.gz? ;)
DEPENDENCIES ;)

Even in gentoo there is a manager of sorts that keeps track of the dependencies even though EVERY thing is built from source just like your .tar.gz file.

---

### Post by Nicolas.Perrault on 2010-02-06
Dependencies? What's that?

---

### Post by mushwars on 2010-02-06
lets say you install kde well you are not just installing KDE you are also installing programs that the program KDE depends on. If you build from source and it requires a dependency it wont work with the one in ubuntu because the paths are all different and they dont work together.

(if I am wrong please put me in my place)

---

### Post by phillychease on 2010-02-06
app runner!
[http://lifehacker.com/5224675/app-runner-makes-launching-linux-executables-easier](http://lifehacker.com/5224675/app-runner-makes-launching-linux-executables-easier)
[http://hacktolive.org/wiki/Runner](http://hacktolive.org/wiki/Runner)

---

### Post by abyrne on 2010-02-06
> **Nicolas.Perrault said:**
> By the way, why should I avoid installing through .tar.gz?

Not to mention updates and uninstallation.

---

### Post by Paqman on 2010-02-06
> **Nicolas.Perrault said:**
> 
By the way, why should I avoid installing through .tar.gz? ;)

As mentioned, it breaks the dependency system of the package manager, which can make your system unstable. Installing from source also means you won't get updates through the automatic update system, and the app will probably break if you upgrade to the next version of Ubuntu. It's also much easier to remove software that you installed through the package manager.

I'd still advise using the version in the repos. 1.5 is the latest stable release, 1.99 is a Beta.

---

### Post by Linux000 on 2010-02-06
> **Nicolas.Perrault said:**
> Dependencies? What's that?

Yeah, forgot about them.

---

### Post by Nicolas.Perrault on 2010-04-16
> **Paqman said:**
>  I'd still advise using the version in the repos. 1.5 is the latest stable release, 1.99 is a Beta.

Yeah that's what I did and it works fine. Thanks guys!

---

