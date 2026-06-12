---
title: "how to Install borland c++ 3.0 on ubuntu"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by vickypark on 2008-12-27
Guys i need to know whether it is possible to install borland c++compiler or should i swithch to an alternative.............please name the alternative

---

### Post by mali2297 on 2008-12-27
The standard C++ compiler in Linux is called g++. Install the package **build-essential** via the the package manager and you will get this compiler as well as other essential tools.

If you also want an [IDE]("http://en.wikipedia.org/wiki/Integrated_development_environment"), there are anjuta, code::blocks, geany among others to choose from. See 
[http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B](http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B)

---

### Post by vickypark on 2008-12-27
u see i understand nothing that u have written above please simplyfy..............i just installed ubuntu yesterday so i'm a pre-beginner.........so help in a easy way,thnxx in advance

---

### Post by sim-value on 2008-12-27
He saif that You dont need to install borland ..

The standard linux compiler is g++

you can install it by going to the Terminal and typing
```
sudo apt-get install build-essential
```

BTW C++ is an Platform-dependen Language so i guess you wont come far coding as youve done under Windows ...

(Java FTW)

/me

---

### Post by vickypark on 2008-12-27
thnxx anyway

---

### Post by mali2297 on 2008-12-27
> **vickypark said:**
> u see i understand nothing that u have written above please simplyfy..............i just installed ubuntu yesterday so i'm a pre-beginner.........so help in a easy way,thnxx in advance

Then I suggest that you first get acquainted with Ubuntu and learn stuff like installing packages from the repositories, see for example 
[http://psychocats.net/ubuntu/](http://psychocats.net/ubuntu/)

When you are ready you can find information about programming at [http://ubuntuforums.org/showpost.php?p=1983565](http://ubuntuforums.org/showpost.php?p=1983565)
 and [http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635).

---

### Post by ashwin.kj on 2009-01-06
> **vickypark said:**
> Guys i need to know whether it is possible to install borland c++compiler or should i swithch to an alternative.............please name the alternative

Is your reason for the want of borland c++ 3.0 to start to learn prog or to exercise what u have already learnt.
In case of second there is prob no compiler in c++ that can stand a substitute 4 borland as it uses old standards.

try the link below .It gives step by step instruction on how to install turbo c++ .I think it should do the trick.
[http://dogbuntu.wordpress.com/2007/0...-ubuntu-linux/](http://dogbuntu.wordpress.com/2007/0...-ubuntu-linux/)

Add [SOLVED] if U got a satisfactory answer

---

### Post by amityadav9314 on 2010-10-04
Hi!
if you really wanna that borland complier in your ubuntu then go for this...
Download "dosbox" and install it.
Then click to open the dosbox from ...menu-->games-->dosbox emulator.

once the dosbox is opened, paste the already unzipped folder of TC under your home folder.

then hit alt+enter command to maximize your dosbox windows.
then type the followin' commands....

mount c ~    ...hit enter
c:            ...hit enter
cd c:\tc\bin  ....hit enter
tc              ...hit enter
and you will be done....

one thing you need to do to change the shortcut key to run the program, i.e. cntrl+f9

you can do that later as well.
if you dont do this then dont you ever press this command to run.
use an alternative way to run your program...click on run tab on upside


enjoy...

---

### Post by lkraemer on 2010-10-04
The previous link is:
[http://dogbuntu.wordpress.com/2007/07/05/using-dosbox-to-run-turbo-c-in-ubuntu-linux/](http://dogbuntu.wordpress.com/2007/07/05/using-dosbox-to-run-turbo-c-in-ubuntu-linux/)

lk

---

