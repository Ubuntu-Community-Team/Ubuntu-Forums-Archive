---
title: "First time compiling from source."
date: 2009-02-01
forum: New to Ubuntu
---

### Post by LucidLoon on 2009-02-01
Hello. 
     I have never compiled a program from source code and would like to try my hand at it. I've got the command line under control enough I'm comfortable I can do it. Does anyone have any suggestions as to a program that compiles easily with a very low number of dependencies to chase after? (ideally zero). I don't care what the program does. I just want to see what compiling a program from source looks like.
Thanks for the help

---

### Post by &#32 Greg on 2009-02-01
Make sure you have build-essential :)

If the package is good, then compiling a program from source should be as easy as ./configure, make, make install.

---

### Post by andrew.46 on 2009-02-03
Hi,

Better might be to install something a little more complex under guidance. There are some great guides on these forums that will do just that, and the better ones will also show the required dependencies. Can I suggest the following:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

which will demonstrate for you:

[LIST=1]
[*]Compiling from source
[*]Use of checkinstall to install the compiled source
[*]Manipulation of a git repository
[/LIST]

And as a bonus you will get a cutting edge audio/video conversion tool :-).

Andrew

---

### Post by LucidLoon on 2009-02-07
Thanks Andrew.46. I checked out this link and it looks straightforward. I'll give it a shot and post back how it goes. 
Thanks again.

---

