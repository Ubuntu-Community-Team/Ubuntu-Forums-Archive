---
title: "installing ubuntu inside windows"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by Capitolman on 2011-01-12
A friend tried to install ubuntu using wubi. He said that it destroyed his hard drive, causing clicking noise`s.
Has any one heard of this before and if so how do you fix it.
As far as my experience goes i down loaded the iso,burnt to disk and using wubi installed in side windows 7 ultimate with out problems.

---

### Post by synicalx on 2011-01-12
Clicking noises sounds like a mechanical fault rather than a software fault (although it could be). Only way Ubuntu could 'destroy' a hard drive is if the installation went wrong either by something undesirable happening (say a power outage in the middle of it all) or by user error (accidentally reformatting the entire drive).

If you've got a dual core machine with 2gb+ of RAM, then the best way to try Ubuntu is probably just in a virtual machine. Virtualbox is free and will allow you to install and/or try more or less any operating system within Windows without having to reboot.

---

### Post by themusicalduck on 2011-01-12
I can't know for sure, but I think it's very unlikely WUBI will have caused the hard drive to break.

When my drive started making loud clicking noises, I had to send it back because it was just a faulty drive.

---

### Post by Capitolman on 2011-01-12
That was what i thought, i did not think it could cause the problem he described i will get the full text of what he said and post it here.

---

### Post by Capitolman on 2011-01-12
Full text of his email:
nightmare - its ruined my hard drive... i noticed clicking whirring noise very quite only audible in silence when the drive was idle- turns out to be a bug in most hard drives that windows fixes but linux doesnt... trying to fix it using special codes to disable aggressive power management hasnt worked and now in windows there is constant random clicks that wernt there before and i think its these codes ive been trying but not sure...early days...- launch your firefox in linux then in complete silence stick your ear to laptop or pc and listenfor this super fast clicking noise usally happens after 6 seconds idle - for me it repeated every ten seconds after finishing - this destroys your hard drive and after much research im of the conclusion that it is linux code not working correct but linux developers refuse to accept it and blame hard drive manufactures... setting deliberate agrresive head parking after 6 seconds idle time which reduces hard drive life dramatically but saves power??? why cant linux developers just do what windows does? actually as im writing this windows 7 seems to have stopped and back to normal PHEW! There is a fix that works for some linux users thats what i tried but it didnt work for me hdparm - b dev/sda/ 254 or 255 both didnt work

be warned... it could be destroying your drive too...

I am at a complete loss as to what has happened to him as my installation using wubi went as smooth as silk. any help would be much appreciated.

---

### Post by matt_symes on 2011-01-12
Hi

Get him to check the SMART status of his hard drive. A clicking hard drive usually means it's failing.

I am interested. What sources did he find to blame Ubuntu?

Kind regards

---

### Post by muteXe on 2011-01-12
[http://www.sammynetbook.com/forum/threads/8073-Linux-UBUNTU-quot-load-cycle-quot-bug-don't-let-it-kill-your-hard-drive](http://www.sammynetbook.com/forum/threads/8073-Linux-UBUNTU-quot-load-cycle-quot-bug-don't-let-it-kill-your-hard-drive)!

Something like this?  I had this a few versions ago where I did actually use a command like "hdparm - b dev/sda/ 254" to stop the clicking.

I've not added anything since installing 10.04, and dont have any of the symptoms.

edit: should have metioned I experienced this in a proper install.  I've never used wubi.

---

### Post by matt_symes on 2011-01-12
Hi

@mutexe. Interesting link. Did you have a laptop or desktop? It is quite old though.

Kind regards

---

