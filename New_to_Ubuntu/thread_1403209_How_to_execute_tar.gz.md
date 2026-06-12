---
title: "How to execute tar.gz??"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by navaneethan on 2010-02-10
How to execute all tar.gz files in ubuntu?? I downloaded some packages in .tar.gz format?? i referred some manuals but it doesn't work!!

---

### Post by Cheezespread on 2010-02-10
These are zipped tarballs. You need to extract the contents to view them . It can include anything in them - manuals like man pages , or source codes of some apps ( which you can compile)

cd into the directory where you have this file.
tar -zxvf  <name_of_file>.tgz

If you dont like to use terminal , you can very well right click on the file and select extract .;-)

---

### Post by Satoru-san on 2010-02-10
You want to make sure you cant find it in repostitories first that are not default on ubuntu, then look and see if there is a .deb version of it anwhere.

After you are sure that you can only install it from source do this

```
mkdir ~/opt/
cp /path/to/.tar.gz ~/opt/
cd ~/opt
tar xvzf file.tar.gz
cd filefolder
./configure
make
sudo make install
```

---

### Post by Cheezespread on 2010-02-10
> **Satoru-san said:**
> You want to make sure you cant find it in repostitories first that are not default on ubuntu, then look and see if there is a .deb version of it anwhere.

After you are sure that you can only install it from source do this

```
mkdir ~/opt/
cp /path/to/.tar.gz ~/opt/
cd ~/opt
tar xvzf file.tar.gz
cd filefolder
./configure
make
sudo make install
```

It might not always be source codes i believe. Firefox is an exemption.

---

### Post by navaneethan on 2010-02-10
> **Satoru-san said:**
> You want to make sure you cant find it in repostitories first that are not default on ubuntu, then look and see if there is a .deb version of it anwhere.

After you are sure that you can only install it from source do this

```
mkdir ~/opt/
cp /path/to/.tar.gz ~/opt/
cd ~/opt
tar xvzf file.tar.gz
cd filefolder
./configure
make
sudo make install
```

Here what is mean by ~(this symbol)? why the opt? what is it's purpose?

---

### Post by juancarlospaco on 2010-02-10
You cant execute .tar.gz

You can extract .tar.gz

.tar.gz can contain several things

some source code are distributed using .tar.gz, is oriented to developers

very few apps are distributed using .tar.gz, is for standalone or selfcontained apps

.tar.gz is just like a .zip

~ = $HOME = /home/*your-username* = *"your home folder"*

if you some day use make install, i suggest you use checkinstall, 
wich makes a .deb, easy to uninstall cleanly

---

### Post by Satoru-san on 2010-02-10
> **navaneethan said:**
> Here what is mean by ~(this symbol)? why the opt? what is it's purpose?
For me if I cant find an ebuild, simmilar to .deb, I will extract and install them in my home opt folder.

[http://www.linuxtopia.org/online_books/linux_beginner_books/linux_filesystem/opt.html](http://www.linuxtopia.org/online_books/linux_beginner_books/linux_filesystem/opt.html)

^ that will explain my logic...

> This directory is reserved for all the software and add-on packages that are not part of the default installation.

---

### Post by navaneethan on 2010-02-10
> **Satoru-san said:**
> You want to make sure you cant find it in repostitories first that are not default on ubuntu, then look and see if there is a .deb version of it anwhere.

After you are sure that you can only install it from source do this

```
mkdir ~/opt/
cp /path/to/.tar.gz ~/opt/
cd ~/opt
tar xvzf file.tar.gz
cd filefolder
./configure
make
sudo make install
```

It doesn't work .it shows no sch a file or directory ...there is no file in the directory like this above

---

### Post by Cheezespread on 2010-02-10
Did you extract the file as i mentioned ?

---

### Post by 3rdalbum on 2010-02-10
Please listen.

Don't download programs in a .tar.gz file. Programs distributed like this are just source code that needs to be compiled before it can be run. You are not experienced enough to compile software.

Instead, look under the Applications menu at Ubuntu Software Center. You can download and install a massive variety of software using this program. Just find a program you want to try, and hit Install, and that's it.

This is one of the ways where Linux differs from Windows. On Linux, you don't trawl the web to find software; you use your package manager (on Ubuntu, it's Software Center or Synaptic, which both search and install the same software).

---

### Post by Dan_Dranath999 on 2010-02-10
i think he's trying to compile a file named "pathto.tar.gz"

just get a *.deb through the Download Center!

---

### Post by navaneethan on 2010-02-16
yaa i extracted..

---

### Post by navaneethan on 2010-02-16
> **3rdalbum said:**
> Please listen.

Don't download programs in a .tar.gz file. Programs distributed like this are just source code that needs to be compiled before it can be run. You are not experienced enough to compile software.

Instead, look under the Applications menu at Ubuntu Software Center. You can download and install a massive variety of software using this program. Just find a program you want to try, and hit Install, and that's it.

This is one of the ways where Linux differs from Windows. On Linux, you don't trawl the web to find software; you use your package manager (on Ubuntu, it's Software Center or Synaptic, which both search and install the same software).

friend here i am talking about offline installation??? in tar.gz format

---

### Post by navaneethan on 2010-02-18
ya..i done it

---

### Post by Soul-Sing on 2010-02-18
please try a native .deb (ubuntu .deb)instead of a tar.gz.
What program do you want to install? Maybe there are native ubuntu alternatives.
Mind: using tar gz programs you have to take care of updates, security updates yourself.

---

