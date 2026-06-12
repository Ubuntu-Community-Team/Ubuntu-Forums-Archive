---
title: "Installation Problem..headache..HELP!!!"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by cLaRe on 2008-12-29
im trying to installing thing in my ubuntu and i got the following error message. can someone explain what it means and what should i do?? thanks!!!!!


  make: *** No rule to make target `/home/wanqing/packages/ffmpeg/libavformat/avformat.h', needed by `ffmpeg.o'. Stop.

---

### Post by kelean on 2008-12-29
What are you system specs.  What are you tiring to install the OS or firefox?

---

### Post by cLaRe on 2008-12-29
> **kelean said:**
> What are you system specs.  What are you tiring to install the OS or firefox?

actually I'm trying to install a package called FFMPEG so that the C compiler in my ubuntu can perform installation for image processing.

---

### Post by kelean on 2008-12-29
Im not sure how you are tring to install it.  That package in in the repo's.  If you open synaptic and search for ffmpeg then click it and install it.

---

### Post by adult swim on 2008-12-29
ffmpeg is available in the repositories so you could install it with ```
sudo apt-get install ffmpeg
``` unless there is a reason that you are building it

---

### Post by cLaRe on 2008-12-30
e. Download the LAME library from sourceforge

[http://sourceforge.net/project/showfiles.php?group_id=290](http://sourceforge.net/project/showfiles.php?group_id=290)
The latest stable version is lame-3.97.tar.gz

f. Unpack and install
$tar zxf lame-3.97.tar.gz
$cd lame-3.97
$./configure
$make
$sudo make install

g. copy ffmpeg source code from the CD,

h. Build ffmpeg with LAME
$cd ffmpeg
$./configure --enable-libmp3lame
$make
$sudo make install


**The above are the instruction that I followed to install the ffmpeg. Im stuck at the $make at instruction h which gave me the errors i posted earlier**

---

### Post by sam_delta on 2008-12-30
u tried running make as root ("sudo make")? 

but i dont see the point on following that procedure when you can just install it from repos
```
sudo apt-get install ffmpeg
``` <-- this single command will install ffmpeg, or if you prefer a gui, you can go into system > admin> synaptic package manager, search for ffmpeg, check for installation and click on apply

sam

---

### Post by cLaRe on 2008-12-30
> **sam_delta said:**
> u tried running make as root ("sudo make")? 

but i dont see the point on following that procedure when you can just install it from repos
```
sudo apt-get install ffmpeg
``` <-- this single command will install ffmpeg, or if you prefer a gui, you can go into system > admin> synaptic package manager, search for ffmpeg, check for installation and click on apply

sam

I tried the "sudo make" before but it still give problem. I will try the installation from the repos like you mention and let you know later. Thanks alot.

---

### Post by sam_delta on 2008-12-30
alright, id like to hear how it goes, enjoy ubuntu

sam

---

### Post by cLaRe on 2008-12-31
> **sam_delta said:**
> alright, id like to hear how it goes, enjoy ubuntu

sam

it still doesnt work. however, i do feel weird how come the error point to directory "wanqing" but in actual fact tat i dont have such directory in my ubuntu. how can i change it??

what should i do??

---

### Post by sam_delta on 2008-12-31
im not sure whats going on, but have yhou tried "sudo apt-get install ffmpeg"?

sam

---

