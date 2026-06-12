---
title: "Cheese webcam booth freezes up?"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by jakeeee on 2010-04-16
Everytime I try and record video it freezes up.
If it doesn't make me force quit, the videos only like 2 seconds when I was recording for about a minute..
Anyone have a suggestion?

---

### Post by no2498 on 2010-04-16
try this program wxcam
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

getdeb also has it

and do not uninstall cheese it has all the webcam settings
just do not open it

hope this helps

---

### Post by jakeeee on 2010-04-16
```

jake@jake-pc:~$ sudo dpkg -i /home/jake/Downloads/wxcam_1.0.4_i386.deb
(Reading database ... 148894 files and directories currently installed.)
Preparing to replace wxcam 1.0.4 (using .../Downloads/wxcam_1.0.4_i386.deb) ...
Unpacking replacement wxcam ...
dpkg: dependency problems prevent configuration of wxcam:
 wxcam depends on libmjpegtools0c2a (>= 1:1.8.0); however:
  Package libmjpegtools0c2a is not installed.
 wxcam depends on libwxbase2.8-0 (>= 2.8.8.0); however:
  Package libwxbase2.8-0 is not installed.
 wxcam depends on libwxgtk2.8-0 (>= 2.8.8.0); however:
  Package libwxgtk2.8-0 is not installed.
 wxcam depends on libxvidcore4 (>= 1:1.0.0-0.0); however:
  Package libxvidcore4 is not installed.
dpkg: error processing wxcam (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 wxcam



```


Thats what I get when I try to install that wxcam thing :(
Help? :o

---

### Post by jakeeee on 2010-04-16
Neverminid. I guess that just means I have to install the dependincies right?
Well I hope this will work :)

---

### Post by jakeeee on 2010-04-16
wxcam has a dependincie that doesnt exist?
libmjpegtools0c2a

I cant find that package.
And I need it for wxcam.
What do i do?

---

### Post by edcompsci on 2012-05-18
Mine too. I installed wxcam but can't get any audio. I get audio on cheese, but the video freezes while recording. I'm going to report a bug.

---

### Post by Derek Karpinski on 2012-05-19
install guvcview instead of cheese.

---

