---
title: "Non-executing executable."
date: 2009-01-05
forum: New to Ubuntu
---

### Post by rtneyhart on 2009-01-05
I was looking for something to use in Linux in place of Quicken and came across GNUCash.  I didn't care for it and thought I'd try something else.  I downloaded and extracted Check Book Tracker, but the executable doesn't work.  I tried double-clicking on the cbtracker icon, right-clicking on the icon and tried opening it with the Autorun Prompt, and even tried going to the directory it is in and typing cbtracker in Terminal.  I checked the properties of the file and the run-as-executable box is checked.  What should I do now?  Help!

Russ
Intel Mac Mini 1.66 GHz / 2 GB / Ubuntu 8.10

---

### Post by donkyhotay on 2009-01-05
If you just downloaded and extracted it did you make certain to:
```
cd directory_you_extraced
./cbtracker
```
and if you did that and it failed what was the terminal output you recieved? Usually when a program fails to launch running it from the CLI will give you the information you need to find out what went wrong.

---

### Post by The-IRS on 2009-01-05
is it a windows application?
.exe files typically are and can only be opened with the wine application for linux.

Here's a link on how to install it:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by donkyhotay on 2009-01-05
It isn't a windows executable but a linux binary
[http://freshmeat.net/projects/cbtracker/](http://freshmeat.net/projects/cbtracker/)

//edit: well... at least I assume thats the program rtneyhart is trying to use

---

### Post by bodhi.zazen on 2009-01-05
You have to make it executable.

chmod a+x ./program

---

### Post by Guille Damke on 2009-01-05
> **bodhi.zazen said:**
> You have to make it executable.

chomd a+x ./program

A small correction, it has to be "chmod" instead of "chomd".

---

### Post by bodhi.zazen on 2009-01-05
> **Guille Damke said:**
> A small correction, it has to be "chmod" instead of "chomd".

:lolflag:

Thanks

---

### Post by rtneyhart on 2009-01-06
Good Morning All,

  Sorry about the confusion...  The file is a Linux binary.  I've tried running it, then making it executable through terminal.  This is the terminal output I received this morning:

rtneyhart@mac-mini:~$ cd Desktop
rtneyhart@mac-mini:~/Desktop$ ls
cbtracker  LW300  LW300~  lw300-2  thunderbird
rtneyhart@mac-mini:~/Desktop$ cd cbtracker
rtneyhart@mac-mini:~/Desktop/cbtracker$ ls
cbt_icon.xpm  cbtracker  help  license.txt  README
rtneyhart@mac-mini:~/Desktop/cbtracker$ ./cbtracker
./cbtracker: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
rtneyhart@mac-mini:~/Desktop/cbtracker$ chmod a+x ./cbtracker
rtneyhart@mac-mini:~/Desktop/cbtracker$ ./cbtracker
./cbtracker: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
rtneyhart@mac-mini:~/Desktop/cbtracker$

  I did a search for "libgtk-1.2.so.0" and found nothing.  Is this a library that I have to download and place somewhere for this binary to use?

Regards,

Russ
Intel Mac Mini 1.66 GHz / 2 GB / Ubuntu 8.10

---

### Post by bodhi.zazen on 2009-01-06
did you read the README ?

Try installing libgtk-1.2 or libgtk-common

---

### Post by rtneyhart on 2009-01-06
I did read the README, but didn't find anything that helped me.  The first paragraph is this:

This is the ELF executable (that means, you run the program "cbtracker" 
from the command prompt or make an icon for it with the included icon 
file in your desktop environment.)

I'll try to find the packages you've suggested and see if that helps.  Thanks.

Russ

---

### Post by bodhi.zazen on 2009-01-06
I hate it when the developers do not take the time to write a decent README :lolflag:

IMO documentation is essential to good application development skills

---

