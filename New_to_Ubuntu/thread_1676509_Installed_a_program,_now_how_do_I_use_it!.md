---
title: "Installed a program, now how do I use it!"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by esedward on 2011-01-27
I found at the link below a description of how to install Latex on ubuntu linux.  I followed the instructions and the download was successful, only now I don't know how to get to the program itself! When I do a search for "latex" I am given a list of nearly 900 files (presumably all the stuff the program itself needs to run) but I cannot find a .exe file. [URL="http://linuxandfriends.com/2009/10/06/install-latex-in-ubuntu-linux/"]http://linuxandfriends.com/2009/10/06/install-latex-in-ubuntu-linux/
[/URL]

---

### Post by mharrison on 2011-01-27
You might give [https://help.ubuntu.com/community/LaTeX](https://help.ubuntu.com/community/LaTeX) a read.

Edit:

This might be better:
[http://www-lmmb.ncifcrf.gov/~toms/latexforbeginners.html](http://www-lmmb.ncifcrf.gov/~toms/latexforbeginners.html)

---

### Post by cherva on 2011-01-27
I suppose after running:
```
$ sudo apt-get install gedit-latex-plugin texlive-fonts-recommended latex-beamer texpower texlive-pictures texlive-latex-extra texpower-examples imagemagick
```
You have to start "gedit" it is in Applications -> Accessories -> Text editor or something like that. ( you can just press Alt+F2 and type gedit)
Then you have to find where the plugins are and enable the newly installed latex plugin and you should be OK.
Again ... I just  suppose that :)
Another thing linux does not use .exe files ... they are windows executables. Linux executables do not have an extension or if they are scripts they probably have something like .sh or .bash ....

---

### Post by esedward on 2011-01-27
thanks all!

---

