---
title: "installation"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by fuse_Man91 on 2010-10-02
Another question for you guys: if I don't want to install a program from the synaptic package manager or the software center, how do I go about installing it through the terminal? Also, I downloaded ktorrent from the package manager but when I download a torrent file from the internet, I can't choose ktorrent as a program to open the file with. Why is that? Thanks,

Nathan

---

### Post by Hippytaff on 2010-10-02
> installing it through the terminal? 

Sudo apt-get {appname}

---

### Post by Hippytaff on 2010-10-02
> installing it through the terminal? Sudo apt-get {appname}

Don't know why it posted twice :-s

---

### Post by SnakeEye on 2010-10-02
about the installation of the softwares through terminals you have multiple choice

you can open terminal : then type :

sudo apt-get install <Program name>

or

sudo aptitude install < program name>

if you've downloaded debian package you can type the following :

dpkg < the full name pf package.deb > that you've downloaded if u need further help

feel free to ask

---

### Post by Hippytaff on 2010-10-02
I've read up on this and can't fathom how aptitude and apt differ? this should probably be on another thread but any ideas :-)

---

### Post by fuse_Man91 on 2010-10-02
Thanks guys, that seemed to work. Do both the sudo apt-get and the sudo apt-get install both work the same way? Also, what about programs that have different names than the program suggests? Such as "mozilla_firefox" for the firefox web browser (just an example).

---

