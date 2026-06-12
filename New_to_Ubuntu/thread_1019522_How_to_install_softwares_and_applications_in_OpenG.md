---
title: "How to install softwares and applications in OpenGenu or Ubuntu"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by bluecarin on 2008-12-23
Hello Guys, 
I am absolute beginners and zero knowledge of Linux.

I have installed both OpenGenu and Ubuntu. But the problem is that i cant install any software on Ubuntu.

Here are my questions::

1) i dont have internet connection so i have downloaded every software package i need. Since every file comes in tar.gz format or .zip for mat i can't install any software on it.
2) Please help me installing  these software packages on my Ubuntu. 

To name a few i have packages like ::

aTunes, VLC media player etc.

I know how to install .Deb packages since they are damn easy and get installed by one click.

Please support me for installing tar.gz or .zip or any other extension file,

Thanks.

---

### Post by albandy on 2008-12-23
for tar.gz

tar zxvf file.tgz
then read the "README" file included

for zip

unzip file.zip

---

### Post by bluecarin on 2008-12-23
> **albandy said:**
> for tar.gz

tar zxvf file.tgz
then read the "README" file included

for zip

unzip file.zip
I am not able to understand the Readme. its written to use .sh file but i am not getting any help.

Can u help me by giving any example to install a software.

Thanks

---

### Post by albandy on 2008-12-23
for example:
tar zxvf mydownloadedprogram.tgz
cd mydownloadedprogram
more README (bla bla bla, user config, bla bla bla, dependecies ....)
./configure
make
make install

now if you satisfaied all program dependencies the software is installed.

Before compiling or installing tar.gz files I think you should read some Linux command line documentation.

Usually tar.gz programs are sources, so you should compile it.

You will need the required compiler and the required libraries. 
Is for this that is important to understand and know how the compiler and the command line commands works

---

