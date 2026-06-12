---
title: "Problem when compiling program"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by aero528 on 2009-01-03
I am using Ubuntu 8.10 and I'm trying to compile the source code to RemotePad(which is a pretty neat iphone thing where you can use the iphone as a mouse).  I've looked at plenty of tuts on how to compile, and I get stuck at the ./configure part.  I type in 

./configure

 it gives me this... 

bash: ./configure: No such file or directory   

Everything else makes sense, but that.  What am I doing wrong?  I got the build-essentials through synaptic.  To be honest I have no clue what I'm doing!  Thanks for any help!

---

### Post by taurus on 2009-01-03
1.  Are you in the right directory when you ran that command?

2.  Is there a README or INSTALL since not everything requires you to run the ./configure command?

---

### Post by aero528 on 2009-01-03
I'm in the directory that I extracted the source code to.  There is no readme or install, I looked for that.  When I run make without the ./configure I get this....

cc -L/usr/X11R6/lib -L/usr/X11R7/lib -L/usr/X11/lib -lX11 -lXtst -lm  remotepad.o   -o remotepad
/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make: *** [remotepad] Error 1

Any other ideas?  Thanks!

---

### Post by sagarp on 2009-01-12
i'm not sure if you found your solution, but you're getting this error because you need to install xtst first. do this:

```
sudo apt-get install libxtst-dev libxtst6
```

i don't know if you really need libxtst6, but it can't hurt. after that, just run make and it should compile with no problems.

-sagar

---

### Post by Fatal Equinox on 2009-07-09
> **aero528 said:**
> I'm in the directory that I extracted the source code to.  There is no readme or install, I looked for that.  When I run make without the ./configure I get this....

cc -L/usr/X11R6/lib -L/usr/X11R7/lib -L/usr/X11/lib -lX11 -lXtst -lm  remotepad.o   -o remotepad
/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make: *** [remotepad] Error 1

Any other ideas?  Thanks!

When i did it i noticed that the true command was 
```
./X11/configure 
```
But now i am stopped at make command   i get
```
make: *** No rule to make target `remotepad.o', needed by `remotepad'.  Stop.
```

So i have not installed successfully yet...

---

### Post by boblemur on 2009-07-09
aero528, try running 

```
./X11/configure
```

as was suggested, and post the result, also it would help if u showed us what tutorial you were trying to follow, so i or someone else can run through it ourselves.


Fatal Equinox:

attatch the makefile ( or at least paste the contents here) please, and do you have build essentials etc and the packages listed in the above post installed? even though make should still have a rule for it regardless.

---

