---
title: "Error: libgudev not installed but I installed it (hope so)"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by Zirthang on 2010-06-16
What does it mean?  I installed libgudev 1.0.0 in ubuntu 10.04 but showing error while configuring cheese.
.....
........
..........
checking for UDEV... no
checking operating system... Linux
configure: error: libgudev is required under Linux and not installed


 Tried to figure it out.:confused: (check the screenshot pls)


[IMG]file:///home/zirthang/Desktop/Screenshot.png[/IMG][IMG]file:///home/zirthang/Desktop/Screenshot.png[/IMG]

---

### Post by anewguy on 2010-06-16
I don't know if it will help or not, but you could try the following in a terminal window:

sudo ldconfig <press enter>

According to a slightly earlier post that is supposed to re-index the libraries if you are having problems.

Dave ;)

---

### Post by Zirthang on 2010-06-16
I tired with sudo ldconfig but nothing happened
anything else that I should try to configure???:-k

---

### Post by anewguy on 2010-06-16
I suppose you could always see if apt-get will pick up a different version or something for cheese, but I think I would also update/upgrade first:

sudo apt-get update <press enter>

sudo apt-get upgrade <press enter>

sudo apt-get build-dep cheese <press enter>


Dave ;)

---

### Post by Zeike on 2010-06-16
You're trying to compile a program so you need to install the libgudev headers & development files as well.

These can be found in the package 'libgudev-1.0-dev' I think.

Generally when compiling from source you need to have both package 'x' and the corresponding 'x-dev' package.

---

### Post by ovidiugabriel on 2012-06-06
I also encountered this problem on Fedora. It is not and Ubuntu specific error. ):P 
I still have no idea how to solve it exactly. Usually it works by downloading -dev package (at least on ubuntu :-({|=)

---

