---
title: "installing qt in ubuntu"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by manish411 on 2011-05-26
I am starting to learn building gui applications in qt. I have worked in building swing applications using java. 
1. I need to install qt libraries.
2. I need some links on some tutorials

thanks

---

### Post by 1991sudarshan on 2011-05-26
Unfortunately you can not install using apt! Try this link! You do not have to search for tutorial! When you install qt, you get tutorial along with the installation. The installation file in a bin file. use this command to install

[B]chomd +x filename.bin
./filename.bin 
[/B]

[http://qt.nokia.com/downloads/](http://qt.nokia.com/downloads/)

---

### Post by manish411 on 2011-05-26
I did 
$apt-get install qt4-dev-tool
would that install all the libraries needed??
that also installed a 64 MB qt doc .
where can i find that file ??

---

### Post by 1991sudarshan on 2011-05-26
Hope it should! I did the installation through the bin file!

---

### Post by jre6 on 2011-05-26
Apt-get will automatically fetch the stuff required with the libraries and dependencies

---

