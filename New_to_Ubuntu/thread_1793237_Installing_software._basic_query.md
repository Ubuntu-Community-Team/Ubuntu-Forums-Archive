---
title: "Installing software. basic query"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by lemontree45 on 2011-06-29
Hi, I am trying to install a software relevant for my studies.

well I have the files with me and the procedure to do it. I am running Ubuntu in VM Virtualbox. I have downloaded the setup files for this software. 

How do I do the following step. Please help. Thanks

change into the core directory and build the core
./bootstrap && ./configure && make && make install

---

### Post by el_koraco on 2011-06-29
You open a terminal. Hit CTRL ALT T on the desktop. then you go to the folder where you have the files. Say it's in /Downloads/your software. 

cd Downloads/your software

Then you run the commands one after another. 

```
./bootstrap
./configure
make
sudo make install
```

Hopefully you won't get errors on one of the steps. What software is it? Maybe it can be found in the Software Center or as a .deb package.

---

### Post by nothingspecial on 2011-06-29
You need to be in the folder you have extracted.

Then assuming you have the correct packages for building it, just type that commands.

If you are running ubuntu, you will need to do

```
./bootstrap && ./configure && make && [COLOR="Red"]sudo[/COLOR] make install
```

---

### Post by Perfect Storm on 2011-06-29
Hi,

Which software do you want to install? In Ubuntu and other Linux Distro you usually install software/applications through a package manager. Have you checked Ubuntu software center?

---

### Post by lemontree45 on 2011-06-29
Thank you guys for the quick response

Its this software called Iris (Cognitive radio application).

Well,I executed this command

./bootstrap && ./configure && make && make install

and then a new message says 

+ aclocal -I config
./bootstrap: 1: aclocal: not found

any idea? is it about some missing file?

---

### Post by Perfect Storm on 2011-06-29
Have you installed tools for compiling?
Install build-essential this should give you the basic compiling tools.

---

