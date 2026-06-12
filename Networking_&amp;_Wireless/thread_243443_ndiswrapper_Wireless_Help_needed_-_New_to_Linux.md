---
title: "ndiswrapper Wireless Help needed - New to Linux"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by ItsaSpoon on 2006-08-25
After installing the lovely ubuntu I found that it had a problem with my belkin wireless card. After a quick reboot to go into my Windows I googled it and found the problem.

[http://www.gidforums.com/t-4390.html](http://www.gidforums.com/t-4390.html)

I have the files and evreything on ubuntu and after reading the readme.txt and the install.txt I have no idea what it means.

Example:
```
tar zxvf ndiswrapper-0.12.tar.gz
cd ndiswrapper-0.12
make
make install
```
How do I do that and all that other code stuff? In the terminal? :confused: 

It would be nice if you could explain it very detailed because I am a linux newb and really want some help so I can finally delete Windows =D>

oh btw, if it helps, I am using the ubuntu 6.06 amd64


Ok :) made a little progress I know what i'm doing.
I just have one problem now. While in the terminal: bash:      ndiswrapper command could not be found

this happens when i do ndiswrapper -i \bcmwl5.inf

and the make and makeinstall stuff doesn't work I think because nothing comes up

---

### Post by ddales on 2006-08-29
I'm assuming you have a 64bit Ubuntu installed.  

Your ndiswrapper and card driver types have to match.  You cannot use 32bit wireless drivers with a 64bit ndiswrapper and vice versa.  Since very few wireless cards provide 64bit drivers, unless yours does, forget it.  It will never work.

---

### Post by anansi on 2006-08-29
first of all

you want to see this brilliant wiki.

[http://wiki.clug.org.za/wiki/Creating_a_WiFi_Node_from_a_linx_box](http://wiki.clug.org.za/wiki/Creating_a_WiFi_Node_from_a_linx_box)

notice at the start of the wiki you do a 

 apt-get install ndiswrapper-utils

this should make ndiswrapper work in terminal, the debian/ubuntu way

---

