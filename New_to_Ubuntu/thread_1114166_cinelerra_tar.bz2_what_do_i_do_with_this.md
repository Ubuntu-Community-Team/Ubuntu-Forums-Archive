---
title: "cinelerra tar.bz2 what do i do with this ?"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by klein de usa on 2009-04-02
hi 
   i downloaded this file from the cinelerra web sight (cinelerra-4-ubuntu-amd64.tar.bz2) and it is on my desktop and i have no idea how to install it?
   i'm prety sure i need to unpack it somewhere, do i need to make a directory and put it there? then what ?

---

### Post by oldos2er on 2009-04-02
It's probably easier to use a package manager: [http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

---

### Post by Hospadar on 2009-04-02
I second that emotion.

What you downloaded is a source package (which is just a generic term for any folder or archive containing source code of any sort), you'll need to unpack it, get all the build dependancies (start with build-essential), then build it, depending on the package this can be pretty complicated (and since cinelerra is huge and complicated, I suspect building it will be).  

Anywho, there is probably a readme in the source package that might help you if you really wanted to go that route.  But again, probably a lot easier to just install it with a package manager.

---

### Post by nothingspecial on 2009-04-02
Yep, I third that, do it from the repos.

But if you want to have a go, try clicking (can`t remember if it`s double or single) it and you should be asked if you want to unpack or extract it. Once you`ve done that find the README file and read it. That should tell you what to do

---

### Post by klein de usa on 2009-04-02
hi 
   it ended up being really easy, i created /home/klein/install/ directory and used file roller to unpack the files there. 
   to run cinelerra in terminal typed cd /home/klein/install/cinelerra-4-ubuntu-amd64/ then type ./cinelerra and it runs there was no install just unpacking.
   then i created a launcher on my desktop to start it 
   i'm running 8.04.1 and when i ran cinelerra it gave me a error on start up i followed this link and fixed the error [http://ubuntuforums.org/showthread.php?t=501633]("http://ubuntuforums.org/showthread.php?t=501633")


i don't think the package was in the repos for 64bit i checked that is why i was trying to install it this way! thanks guys

---

