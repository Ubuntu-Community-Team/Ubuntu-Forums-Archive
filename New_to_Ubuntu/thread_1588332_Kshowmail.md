---
title: "Kshowmail?"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by Greg Mueller on 2010-10-04
Trying Ubuntu again. I'm all updated and ready to go got everything all downloaded and installed, but still don't know much about it. 

I saw a thread about ***Kshowmail*** and it being like Mailwasher. I doownloaded it to my desktop where it sits now. 

Can someone help me with some instructions on how to install it?

Just having messed with 10.04 today, it looks like it has come quite away

Please keep the comments simple as I don't know a lot about how to do all this stuff and it'd been some time since I even tried.

Thanks

---

### Post by andrewthomas on 2010-10-04
Read this first

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Then this

```
sudo apt-get update && sudo apt-get install build-essential checkinstall kdepimlibs5-dev kdepimlibs5 cmake
``` Then you probably want to do 
> 
Installation:
-------------
tar xzf kshowmail-4.0.tar.gz
cd kshowmail-4.0
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix=/usr/bin` 
( or you could pass it the /usr/local/bin prefix )
make
**sudo checkinstall**



---

### Post by Greg Mueller on 2010-10-04
WooF!

I guess this will take a little doing

---

### Post by Greg Mueller on 2010-12-08
I have downloaded and followed your instructions but I can't get it to install

here's what I get when I put this line in the terminal

greg@Ubuntu:~$ tar xzf kshowmail-4.0.tar.gz




tar: kshowmail-4.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

---

### Post by Greg Mueller on 2010-12-08
Nevermind I got it

---

