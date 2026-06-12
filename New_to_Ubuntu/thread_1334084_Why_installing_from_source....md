---
title: "Why installing from source..."
date: 2009-11-22
forum: New to Ubuntu
---

### Post by emigrant on 2009-11-22
hi all;)
can any one explain me what is the need for 'installing from source'.
and what makes it differ from other ways of installing such as apt-install and dpkg -i.
i only know one thing about it that it doesnt resolve dependancies like dpkg -i.

thank you all
:popcorn:

---

### Post by TironN on 2009-11-22
When installing from source you can edit the source changing the program. Really you only need to if it isn't in the depositories.

---

### Post by MelDJ on 2009-11-22
if there are no .debs for the program too

---

### Post by 3rdalbum on 2009-11-22
Compiling from source has a couple of advantages:

1. You can get programs that aren't in any repositories

2. You can compile the up-to-the-minute snapshot of the program for testing. For instance, if you report a bug in a release version of a program, the developer might say "Compile the latest code from the SVN and see if the bug exists there".

3. You can see the source code and make modifications

4. You can enable additional features of the program that might be experimental or might be purposely disabled in the Ubuntu version (for instance, AAC encoding has been removed from Karmic due to a possible licensing problem... but if you need it, you can compile your own FFMPEG library with it enabled).

5. If you use Linux on a different processor architecture (for instance, PowerPC or ARM) you'll find that most people don't make Debs or PPAs for you. So you'll need to get the source code and compile it. Source code is pretty much the only format that can be made workable on a different processor architecture.

6. The compiled version of the program can be specially optimised for your computer's processor and distro.

---

### Post by andrew.46 on 2009-11-23
7. It can be a huge amount of fun :).

Andrew

---

### Post by XCan on 2009-11-23
8. You may be able to squeeze out some extra performance, normally no wonders but it could be fun.
9. It could really be a huge amount of pain as well. ;)

---

### Post by emigrant on 2009-11-23
thank you all for the suggestion :D.
can anybody suggest me a small app to start testing with??

---

### Post by carml on 2009-11-23
I think you can compare the current version of gedit (it's the default "notepad" for Ubuntu) installed on your PC with the one you compile from source. Gedit should be a very little application and so best suited for your test. :-)

---

### Post by emigrant on 2009-11-23
what is the extension of a source file? 
i mean how can i download it and see which is the sourcefile actually.

---

### Post by ankspo71 on 2009-11-23
Hi,
a source file package usually has a 'configure' file and a 'make' file inside the archive. the archive type could be tar.gz , tar.bz2 etc, or even sometimes a .zip (but that's usually for windows).
James

---

### Post by emigrant on 2009-11-23
hi all,
downloaded the gedit.tar.gz and with the help of some tutorials im gonna try this.
by the way can anybody confirm me that compiliing from source won't ruin my existing gedit?

thank you very much.

---

### Post by carml on 2009-11-23
> **emigrant said:**
> hi all,
downloaded the gedit.tar.gz and with the help of some tutorials im gonna try this.
by the way can anybody confirm me that compiliing from source won't ruin my existing gedit?

thank you very much.

I forgot to say before that if the version you compile is the same of the one installed on your machine,the compiled one could overwrite your existing copy of the program,if something goes wrong you'd to reinstall the SW from the package.
In addition to the infos the other posters gave you, one person can grab the source code of a not yet released version and create a packaged version for simplicity of use, that is what e.g. official mantainers do every time they release a new stable version of the SW. ;)

---

### Post by oldos2er on 2009-11-23
If you haven't seen this information, it might be helpful: 

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by emigrant on 2009-11-23
@ [carml]("http://ubuntuforums.org/member.php?u=684219") :),
my current gedit is 2.26 and the current latest one is 2.28.
say i compiled and installed the latest one from the source, now which one will be the default app? :confused: 
if i do in terminal:
```

sudo apt-get remove gedit

```
which gedit would get removed?

thank you for your time :popcorn:

---

### Post by emigrant on 2009-11-23
> **oldos2er said:**
> If you haven't seen this information, it might be helpful: 

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

thanks for the links, i will have a loot at them now :popcorn:

---

### Post by carml on 2009-11-23
> **emigrant said:**
> @ [carml]("http://ubuntuforums.org/member.php?u=684219") :),
my current gedit is 2.26 and the current latest one is 2.28.
say i compiled and installed the latest one from the source, now which one will be the default app? :confused: 
if i do in terminal:
```

sudo apt-get remove gedit

```
which gedit would get removed?

thank you for your time :popcorn:

It should be the latest one :).

---

### Post by emigrant on 2009-11-23
thank you :popcorn:

---

### Post by Shazaam on 2009-11-23
.debs are nice and easy and darned near foolproof to install but you don't really see what's going on (except a few lines in the terminal output). Compiling from source prints out tons of other info and can help to diagnose errors.

---

### Post by Zoot7 on 2009-11-23
My reason for compiling parts of the gnome desktop and some apps from source is to use different configure options.
For example I always recompile "gnome-applets" from source so I get the Mini-Commander applet, which is like a mini integrated terminal on the panel.

---

