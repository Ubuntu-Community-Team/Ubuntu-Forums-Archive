---
title: "Problem with make &amp;&amp; make install"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Extract_Here on 2009-12-21
this error occurs when I try to make && install
hayden@hayden-laptop:~/Downloads/qbittorrent-2.0.2$ sudo make && make install
[sudo] password for hayden: 
make: *** No targets specified and no makefile found.  Stop.
 

 thanks in advance

---

### Post by synapsys on 2009-12-21
what's contained in that directory?

```
ls
```

---

### Post by snowpine on 2009-12-21
qbittorrent is in the Ubuntu repositories, so:

```
sudo apt-get install qbittorrent
```

should do the trick.

---

### Post by Extract_Here on 2009-12-21
im learning to compile though so i want to compile it for when something isnt in the repository

---

### Post by Extract_Here on 2009-12-21
> **synapsys said:**
> what's contained in that directory?

```
ls
```


its an extracted qbittorrent folder along with tar.gz package

---

### Post by synapsys on 2009-12-21
You can't 'make' anything while its in a tar.gz file. First you must extract it.

```
tar -xvf filename.tar.gz
```

Then navigate to the extracted directory

```
cd filename
```

Then run configure script

```
./configure
```

Then install

```
make && make install
```

---

### Post by Extract_Here on 2009-12-21
I did that already except for the make && make install

---

### Post by synapsys on 2009-12-22
so what's the problem? you're not making much sense......

And why does your sig say "may the source be with you" if you don't even know how to compile a program?

---

### Post by Joeb454 on 2009-12-22
Try running ```
make && sudo make install
``` instead. I can't imagine that being the issue, but it's definitely worth a try :)

---

### Post by Paqman on 2009-12-22
> **Extract_Here said:**
> im learning to compile though so i want to compile it for when something isnt in the repository

If something isn't in the repos you can almost always find a PPA or a deb. I haven't compiled anything in years. I wouldn't say it's a particularly useful thing to know these days.

---

### Post by synapsys on 2009-12-22
> **Paqman said:**
> If something isn't in the repos you can almost always find a PPA or a deb. I haven't compiled anything in years. I wouldn't say it's a particularly useful thing to know these days.

Unless you use security tools.....

maybe he's a hacker...lolz.

---

### Post by doas777 on 2009-12-22
the error you are getting indicates that there is not a section in the makefile entitled "install", or that there is no file in the dir you cd'ed to, called 'makefile'. visually confirm that the file exists in the path expected, and if not, cd to where it is. if it is there, open it up and look for 'install:'

here is part of a makefile that I have lying around:
```

install:
    $(MAKE) -C src $(@)
    $(MAKE) -C scripts $(@)
    $(MAKE) -C manpages $(@)
    @echo " "
    @echo "
[*] Run 'app-update' as root (or with sudo) to install or update from website (Internet connection required)."

uninstall:
    $(MAKE) -C src $(@)
    -rm -fr $(DESTDIR)$(docdir)
    $(MAKE) -C manpages $(@)
    $(MAKE) -C scripts $(@)

strip:
    $(MAKE) -C src $(@)

doc:
    install -d $(DESTDIR)$(docdir)
    install -m 644 $(DOCFILES) $(DESTDIR)$(docdir)

clean:
    $(MAKE) -C src $(@)

distclean: clean

check: 
    $(MAKE) -C src $(@)
    


```note the "install:"
those instructions are the ones you are invoking, when you say "make install" (the initial make builds according to the default profile, all, which clean compiles all packaged code.)

open the makefile and see what compile options there are

---

