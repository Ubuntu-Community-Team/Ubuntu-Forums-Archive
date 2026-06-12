---
title: "self installed program wont start from command line"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by AllWires on 2010-06-05
Hi,

I installed eclipse manually by downloading it from the website and unzipping it into "/usr/local/bin". So the file I want to run is "/usr/local/bin/eclipse/eclipse"

When I check my path variable I see that that directory is already included, but when I type "eclipse" into the command line, it tells me that it is not installed and I should try to download it. Is there something special I have to do other than just moving it into a directory included by a path variable? I tried searching but I guess I couldn't come up with the right keywords.

---

### Post by sgosnell on 2010-06-05
Unzipping it does not install it.  I'm not sure why you want to install it this way in any case.  Eclipse is in the repositories, so you can just 'sudo apt-get install eclipse', or install it through Synaptic.

---

### Post by AllWires on 2010-06-05
> **sgosnell said:**
> Unzipping it does not install it.  I'm not sure why you want to install it this way in any case.  Eclipse is in the repositories, so you can just 'sudo apt-get install eclipse', or install it through Synaptic.

That's true, but the version of eclipse through Synaptic doesn't work with the Android plugin, and the only way to get it to work is to use the versions you can download from the website.

I just want to know how to add a program to the list or file or whatever you use so that I can simply type its name in the console and it will start.

---

### Post by anewguy on 2010-06-05
This link is for 9.04, but the procedures should be the same:

[http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty/]("http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty/")


Dave ;)

---

### Post by sgosnell on 2010-06-05
First, extract the files to somewhere in your home folder, NOT to /usr/bin.  You have to own the files in order to make the package.  Then go to the folder where you extracted the files, and look for a file named 'configure'.  In the terminal, type ```
./configure
```.  This tells bash to run the file in the current folder named 'configure'.  Most packages distributed as archives have such a file.  If it doesn't exist, look for a file named Makefile.  If configure runs, then run ```
make
sudo make install

```and hopefully that will get it installed.  Not the sudo before 'make install', which allows the package to be installed in /usr/bin.  If there is no configure file, just run make and make install.

All this assumes you have build-essential installed.  You have to have that package installed in order to make and compile anything.  What you get in the archive is just source code, so you have to compile an executable, and maybe some shared libraries.

---

### Post by anewguy on 2010-06-05
> **sgosnell said:**
> First, extract the files to somewhere in your home folder, NOT to /usr/bin.  You have to own the files in order to make the package.  Then go to the folder where you extracted the files, and look for a file named 'configure'.  In the terminal, type ```
./configure
```.  This tells bash to run the file in the current folder named 'configure'.  Most packages distributed as archives have such a file.  If it doesn't exist, look for a file named Makefile.  If configure runs, then run ```
make
sudo make install

```and hopefully that will get it installed.  Not the sudo before 'make install', which allows the package to be installed in /usr/bin.  If there is no configure file, just run make and make install.

All this assumes you have build-essential installed.  You have to have that package installed in order to make and compile anything.  What you get in the archive is just source code, so you have to compile an executable, and maybe some shared libraries.

Normally, yes.  But.....if you see the information in the link I provided they don't ever do the configure/make/make install procedures.  I was a little surprised, but it seems to be the case for Eclipse.

For the OP - in the link I posted is also the instructions on creating a file so you can run from the command line.

Dave ;)

---

### Post by sgosnell on 2010-06-05
I see.  It's all java.  

@OP: Do you have a java vm installed?  Looks like it won't run without a good java install.  Have you read this: [http://wiki.eclipse.org/FAQ_I_unzipped_Eclipse%2C_but_it_won%27t_start._Why%3F](http://wiki.eclipse.org/FAQ_I_unzipped_Eclipse%2C_but_it_won%27t_start._Why%3F)  
or the installation instructions  [http://wiki.eclipse.org/Eclipse/Installation](http://wiki.eclipse.org/Eclipse/Installation)

---

