---
title: "packaged vs non packaged apps"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by dimitriv on 2009-03-22
hi

**what are the risks/implications/considerations of using non-packaged apps?**  I've found most things are packaged which is great, but then encountered some which aren't available and require manual install (which i've installed manually ok).

I now realise a bunch of the ones i've manually installed are available through medibuntu (which I hadn't heard of previously). Since medibuntu doesn't always offer the latest application version I'm weighing up for some other apps I want to install whether to use the medibuntu packaged older app version or to choose the manual install (which i know can be a little bit more headache - but once it's installed that's problem solved isn't it?!)

thanks

---

### Post by James_Lochhead on 2009-03-22
Risks/problems:

1) Manually installed apps have not been quality checked by the Ubuntu team like the ones from the PPA. They might have bugs.

2) You have to be careful about installing manually, for the same reason as above. You could install malware (although this is unlikely - not much out there for linux). 

3) You could modify something then forget about it... causing annoying effects. For instance, yesterday I installed the latest version of the JDK manually. Today I removed it and installed the default, only to find out eclipse was broken. 10 minutes later I worked out that it was because I hadn't removed the custom environment variables from /etc/profile.

4) You forget what you have installed.

5) You might have your program installed over if you don't read dependencies. 

Advantages:

1) You can get the exact version of what you want - and not have Ubuntu nag you about it.

2) You can optimise the code for your computer. 

Btw, you know you can build your own .debs pretty quickly using dbpkg?

---

### Post by hyper_ch on 2009-03-22
> **James_Lochhead said:**
> 1) Manually installed apps have not been quality checked by the Ubuntu team like the ones from the PPA. They might have bugs.
Even packaged stuff has bugs ;)

> **James_Lochhead said:**
> 2) You have to be careful about installing manually, for the same reason as above. You could install malware (although this is unlikely - not much out there for linux).
Be suspicious on what you install from outside the official repositories. With the central maintained software you can be sure it has no malware/spyware/viruses/... in it. For everything else you have to trust the source it comes from. usually if the source is also provided then you should be safe..

---

### Post by James_Lochhead on 2009-03-22
> **hyper_ch said:**
> Even packaged stuff has bugs ;)


True but packaged stuff tends to have less bugs. Ubuntu developers wouldn't let a new version of something that was too buggy in the repos.

> **hyper_ch said:**
> 
Be suspicious on what you install from outside the official repositories. With the central maintained software you can be sure it has no malware/spyware/viruses/... in it. For everything else you have to trust the source it comes from. usually if the source is also provided then you should be safe..

Agreed, although there is a minimal amount of that kind of stuff for Linux.

---

### Post by andrew.46 on 2009-03-22
Hi dimitriv,

Perhaps you could mention some specific examples rather than asking in general? I can start the ball rolling by speaking of my own practice of compiling my own copy of MPlayer rather than using the repository version. For a variety of reasons Ubuntu keeps an old version that lacks certain features I need so I 'roll my own'. Of course I then take responsibility for any breakages in my system or any shortcomings in my copy of MPlayer.

Having said that it is still a good idea to actually 'package' the final product so there are no problems with integration with the rest of the packages in the distro. Not always an easy thing to do of course.

All the best,

Andrew

---

### Post by CatKiller on 2009-03-22
Checkinstall is brilliant. When you're installing from source, it makes a package and installs that instead (*sudo checkinstall* rather than *sudo make install*). So you don't forget what you've installed, and you can easily remove it or update it if a newer version becomes available.

---

### Post by hyper_ch on 2009-03-22
```

sudo make uninstall

``` ^^

---

### Post by CatKiller on 2009-03-22
> **hyper_ch said:**
> ```

sudo make uninstall

``` ^^

Doesn't that only work if you've kept the source around?

---

### Post by hyper_ch on 2009-03-22
well, if you compile from sources then I assume you'll also update it regurarly... (svn/cvs/git/...) and then you won't just delete the sources and compiled stuff.

---

### Post by dimitriv on 2009-03-24
I have no plans to install or compile anything from source...

In answer to the question about which apps

64bit Intrepid

*Google Earth
*Real Player
Skype
Flash
Azureus/Vuze

*not installed yet/GE is installed with problems....

Thank you

---

### Post by freak42 on 2009-03-24
biggest advantage of repo software imho is that it gets updated automatically.

hth

---

### Post by dimitriv on 2009-03-24
yes that's a good point, but...  as with the apps listed above, many of the repo versions are not current releases so a manual install may bring you a lot more up-to-date

thanks for the comment

---

### Post by 3rdalbum on 2009-03-24
I once tried to compile a new version of a program, and this program required a new version of "libfreetype". So I compiled that as well, but I must've used the wrong options because the new library stopped all graphical programs from opening. I finally managed to use apt-get to restore the old library.

So, breaking your system is a possibility.

---

