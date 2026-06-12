---
title: "how to do tar.gz install on ubuntu 11.04"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by East Coaster on 2011-05-06
Loaded 10.10 a couple of weeks ago and just upgraded to 11.04. I have saved a tar.gz containing AS2 communications. I need to install it. Read some posts about converting to deb. Not clear. Also downloaded same tar.gz using default Archive Manager and extracted the files. Both extracted files and tar.gz reside under /home/{user}/Downloads. Does anyone have any instructions on where to go from here using either extracted files or raw tar.gz. Tried suggested ./configure etc... didn't work.

---

### Post by ChipOManiac on 2011-05-06
Does The ./configure give any errors?

---

### Post by josephmills on 2011-05-06
did you try to right click on it(tar_.gz) and try and open with ubuntu software center sometimes that helps not all the time though

---

### Post by nickleboyblue on 2011-05-06
Errors:  We need to know what happened when you tried to run ./configure.  Make sure that when you run it, you do so from the directory that came from the tar file's extraction.

Once you've run ./configure (given that there is a configure script), run make, make clean, and make install in the same file (if the directory has a makefile in it)

Essentially, if you're compiling it yourself, the makefile will do all of the compiling for you.  It's just a list of commands, and when you run it, it will execute those commands as if you typed them yourself on the command line.

If it says anything to the effect of "permission denied" when you try to do anything in this, the process might require you to run make as root.  Make sure that you trust the source of the software before you run sudo make.

Note that there is a chance that the file contains the configure script under a different name (which would be rather unprofessional) and you should look at all of the files in your extracted tar directory to see if you can find it.  Most likely it looks something like configure.sh, in which case you would precede it with the ./ that executes the script in order to run it on the command line.

---

### Post by dniMretsaM on 2011-05-06
Make sure you read the README and/or INSTALL files (sometimes they are .txt) and do exactly what it says. Also make sure you have all the dependencies installed.

---

### Post by dudenishad on 2011-08-13
I had the following error when running ./configure

[INDENT]error: Package requirements (gtk+-2.0 >= 2.8) were not met:

No package 'gtk+-2.0' found[/INDENT]

---

### Post by Perfect Storm on 2011-08-13
> **dudenishad said:**
> I had the following error when running ./configure

[INDENT]error: Package requirements (gtk+-2.0 >= 2.8) were not met:

No package 'gtk+-2.0' found[/INDENT]

Usually when you want to compile from source, you need the -dev package(s) of the required libraries.

So in your case it's libgtk2.0-dev that needs to be installed.

But it's a good idea to check if the applications you want to install is available though Ubuntu Software Center first.

---

### Post by realzippy on 2011-08-13
```
sudo apt-get build-dep *packagename*
```

usually installs all compile dependencies you need for compiling that package.

---

### Post by 3rdalbum on 2011-08-13
> **realzippy said:**
> ```
sudo apt-get build-dep *packagename*
```

usually installs all compile dependencies you need for compiling that package.

Only if *packagename* is in the repositories, which isn't the case here.

---

