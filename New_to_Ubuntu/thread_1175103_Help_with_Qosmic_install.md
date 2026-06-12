---
title: "Help with Qosmic install"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by kd0afk on 2009-05-31
I am having tons of problems getting Qosmic up and running. I have been messing with this thing for about 6 hours now.

here is a clipped version of my build return.

Package libxml-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml-2.0.pc'
to the PKG_CONFIG_PATH environment variable

and

Package lua was not found in the pkg-config search path.
Perhaps you should add the directory containing `lua.pc'
to the PKG_CONFIG_PATH environment variable


I have no idea where to put these paths in the qosmic.pro file or 
how to type them so as not to completely bugger up the whole thing.

Also, when I compile and install a program, how do I install it to somewhere besides my Desktop?

---

### Post by kd0afk on 2009-06-01
bump

---

### Post by kd0afk on 2009-06-03
Any help on this?

---

### Post by kd0afk on 2009-06-04
I would really like to know what the hell is going on.
I submitted a problem on the google.code page for qosmic and nobody there could help me get qosmic running. When I try to build qosmic, I get this return on my terminal:

Package lua was not found in the pkg-config search path.
Perhaps you should add the directory containing `lua.pc'
to the PKG_CONFIG_PATH environment variable
No package 'lua' found
Package lua was not found in the pkg-config search path.
Perhaps you should add the directory containing `lua.pc'
to the PKG_CONFIG_PATH environment variable
No package 'lua' found
Package lua was not found in the pkg-config search path.
Perhaps you should add the directory containing `lua.pc'
to the PKG_CONFIG_PATH environment variable
No package 'lua' found


The thing is, nobody can tell me what to add to the file qosmic.pro to make qosmic know where  lua.pc is and evidently nobody here can either. Sad state of affairs.

---

### Post by kd0afk on 2009-06-05
I have been posting on this forum to try and get someone who knows code and syntax to help me out with a problem. Here is the link to the thread I started. [http://ubuntuforums.org/showthread.php?t=1175103&highlight=qosmic](http://ubuntuforums.org/showthread.php?t=1175103&highlight=qosmic)

It is a sad state of affairs to find out that among the 69,163 active members, NONE of them know how to code. Sad sad sad.

I am trying to learn code so maybe this wouldn't be the best place in the world to get answers and learn from.

---

### Post by LewRockwell on 2009-06-05
> **kd0afk said:**
> I have been posting on this forum to try and get someone who knows code and syntax to help me out with a problem. Here is the link to the thread I started. [http://ubuntuforums.org/showthread.php?t=1175103&highlight=qosmic](http://ubuntuforums.org/showthread.php?t=1175103&highlight=qosmic)

It is a sad state of affairs to find out that among the 69,163 active members, NONE of them know how to code. Sad sad sad.

I am trying to learn code so maybe this wouldn't be the best place in the world to get answers and learn from.

69,163 INCLUDING yourself?

perhaps you could pay someone from here([http://www.google.com/webhp?complete=0#complete=0&hl=en&safe=off&num=20&q=qosmic+ubuntu&fp=ycyBJX8HB1U](http://www.google.com/webhp?complete=0#complete=0&hl=en&safe=off&num=20&q=qosmic+ubuntu&fp=ycyBJX8HB1U))...

to help YOU on YOUR timetable/terms...

---

### Post by kd0afk on 2009-06-05
> **LewRockwell said:**
> 69,163 INCLUDING yourself?

perhaps you could pay someone from here([http://www.google.com/webhp?complete=0#complete=0&hl=en&safe=off&num=20&q=qosmic+ubuntu&fp=ycyBJX8HB1U](http://www.google.com/webhp?complete=0#complete=0&hl=en&safe=off&num=20&q=qosmic+ubuntu&fp=ycyBJX8HB1U))...

to help YOU on YOUR timetable/terms...


And STILL no help.

---

### Post by Mornedhel on 2009-06-05
These forums aren't the best place to learn how to code because they are meant to help beginners set up their Ubuntu install and troubleshoot most problems.

For what it's worth, it looks like you didn't install the required libraries, even though the [http://code.google.com/p/qosmic/wiki/BuildAndInstall](http://code.google.com/p/qosmic/wiki/BuildAndInstall) FAQ explicitly mentions them.

Edit: I forgot to mention, thank you so much for being insulting. It always warms my heart when a beginner doesn't understand that everyone here is a volunteer and not everybody can help on a specific issue, and then starts badmouthing the community at large.

---

### Post by albinootje on 2009-06-05
> **kd0afk said:**
> I am having tons of problems getting Qosmic up and running.

They offer a pre-compiled package for Jaunty 64 bit. Why don't you try that first ?

---

### Post by Mark Phelps on 2009-06-05
> **kd0afk said:**
> And STILL no help.

These forums are here to allow us VOLUNTEERS to help folks with Ubuntu-related problems on their PCs.  These are not here to teach folks how to program.

If you want to learn that, go buy a book, or take a course.

---

### Post by pbpersson on 2009-06-05
> **kd0afk said:**
> 

It is a sad state of affairs to find out that among the 69,163 active members, NONE of them know how to code. Sad sad sad.

I am trying to learn code so maybe this wouldn't be the best place in the world to get answers and learn from.

I know how to develop software in BASIC, COBOL, C, Pascal, VB.NET, and Java.

Your question did not in any way relate to creating an application, it was not a coding question.

---

### Post by overdrank on 2009-06-05
Threads merged. Please do not create multiple threads on the same issue. Also be patient as we all are volunteers. :)

---

### Post by smartidiot on 2009-06-05
> **kd0afk said:**
> I have been posting on this forum to try and get someone who knows code and syntax to help me out with a problem. Here is the link to the thread I started. [http://ubuntuforums.org/showthread.php?t=1175103&highlight=qosmic](http://ubuntuforums.org/showthread.php?t=1175103&highlight=qosmic)

It is a sad state of affairs to find out that among the 69,163 active members, NONE of them know how to code. Sad sad sad.

I am trying to learn code so maybe this wouldn't be the best place in the world to get answers and learn from.

Your question had zero coding concerns in it.  It seems like you have an issue with building not coding.  

It looks like you did not install some required libaries when installing Qosmic  It would work better to ask on their forums.

---

### Post by bacardiandwatermelon on 2009-06-05
[http://code.google.com/p/qosmic/issues/detail?id=11](http://code.google.com/p/qosmic/issues/detail?id=11)

---

### Post by kd0afk on 2009-06-05
> **smartidiot said:**
> Your question had zero coding concerns in it.  It seems like you have an issue with building not coding.  

It looks like you did not install some required libaries when installing Qosmic  It would work better to ask on their forums.

I have all of the supporting libraries installed. This is what I got from their forum;

[COLOR=Red]Your problem is not with the Qosmic.  Your problem is installing Qosmic on your Ubuntu
system.  This is a problem that lies between you, your system, and your system's
package manager.  I suggest you contact an Ubuntu developer to get support for
compiling any software from the source code on your Ubuntu system.

[/COLOR]Seeing as the problem is with the file qosmic.pro then I don't think it is an ubuntu problem.
It is a qosmic problem.
So I am not going to get help anywhere. NICE.

---

### Post by kd0afk on 2009-06-05
> **smartidiot said:**
> Your question had zero coding concerns in it.  It seems like you have an issue with building not coding.  

It looks like you did not install some required libaries when installing Qosmic  It would work better to ask on their forums.

Yes, qosmic requires libraries and I have those libraries but I need to tell qosmic.pro where they are.

---

### Post by kd0afk on 2009-06-05
> **pbpersson said:**
> I know how to develop software in BASIC, COBOL, C, Pascal, VB.NET, and Java.

Your question did not in any way relate to creating an application, it was not a coding question.
So, adding new code to a file is not coding? What specifically is it called so I don't get it wrong in the future.

---

### Post by qamelian on 2009-06-05
> **kd0afk said:**
> So, adding new code to a file is not coding? What specifically is it called so I don't get it wrong in the future.
Search in Synaptic for the libraries that it is asking for. You want to install the packages the have the same name but include '-dev' in the file name. These source packages are needed in order for Qosmic to compile against. That is what the errors are telling you. You don't need to edit anything. 

Although you already have the libraries installed, the dev packages are also needed if you are compiling apps against those libraries.

---

### Post by kd0afk on 2009-06-05
> **qamelian said:**
> Search in Synaptic for the libraries that it is asking for. You want to install the packages the have the same name but include '-dev' in the file name. These source packages are needed in order for Qosmic to compile against. That is what the errors are telling you. You don't need to edit anything. 

Although you already have the libraries installed, the dev packages are also needed if you are compiling apps against those libraries.
Thank you very much for the answer. I wish you would have posted earlier. Giving this a shot.

---

### Post by kd0afk on 2009-06-05
Went into SPM and did a search for lua
Checked off everything with -dev at the end of it. Just tried to build it again and got the exact same error. Qosmic needs to know where the file lua.pc is.

---

### Post by kd0afk on 2009-06-05
Screw it. It probably stinks as a program anyway if the people who wrote it can't help get it built. I will just have to wait till a non 64 bit version gets put into a package.

---

### Post by albinootje on 2009-06-05
> **kd0afk said:**
> Screw it. It probably stinks as a program anyway if the people who wrote it can't help get it built. I will just have to wait till a non 64 bit version gets put into a package.

Try contribute to the open source software community by starting e.g. to help with translations for an open source program, help with organizing Linux install-parties, learning to write some code, maintain a package, help testing software, and helping out other people on this forum. 

After that come back here, and hopefully you will have changed your attitude a bit.

---

### Post by kd0afk on 2009-06-05
> **albinootje said:**
> Try contribute to the open source software community by starting e.g. to help with translations for an open source program, help with organizing Linux install-parties, learning to write some code, maintain a package, help testing software, and helping out other people on this forum. 

After that come back here, and hopefully you will have changed your attitude a bit.

O.K. let me get this straight. I am trying to get a program built that nobody can help me on for the past week and aside from one qamelian everyone on this forum who has replied to my thread has been absolutely no help at all. My bad attitude is entirely a product of the ubuntu forums and the people behind qosmic.

---

### Post by qamelian on 2009-06-05
> **kd0afk said:**
> And STILL no help on this. When I post I post nicely. It is the lack of response that increased the tone of my posts. 
The squeaky wheel gets the grease but you people don't notice the wheel till it gets squeaky and then you bitch about the noise.
Everyone on these forums who offers help is a volunteer...a fellow linux user. None of us are under any obligation to help you. I attempted to help you based on past experience compiling from source because I could tell you were frustrated. However, your increasingly belligerent attitude is unlikely to to win any additional help from anyone. 

No, did you install the specific -dev packages relating to the errors you were receiving? If you did, the please post the relevant errors that are appearing when you execute ```
./configure
```

---

### Post by kd0afk on 2009-06-05
Here is the whole terminal return:

[COLOR=Red]shawn@HAL:~$ cd /home/shawn/qosmic
shawn@HAL:~/qosmic$ ./build.sh
Building Qosmic
Project MESSAGE: Generating Makefile for Qosmic version 1.3.3
Project MESSAGE: Qt version : 4.5.0
Project MESSAGE: Default number of rendering threads : 2
Project MESSAGE: Location of flam3-palettes.xml : /usr/share/flam3
Package lua was not found in the pkg-config search path.
Perhaps you should add the directory containing `lua.pc'
to the PKG_CONFIG_PATH environment variable
No package 'lua' found
Package lua was not found in the pkg-config search path.
Perhaps you should add the directory containing `lua.pc'
to the PKG_CONFIG_PATH environment variable
No package 'lua' found
Package lua was not found in the pkg-config search path.
Perhaps you should add the directory containing `lua.pc'
to the PKG_CONFIG_PATH environment variable
No package 'lua' found
g++ -c -pipe -O2 -D_REENTRANT -w -I/usr/include/libxml2 -I/usr/include/libpng12 -I/usr/include/libxml2 -DNTHREADS=2 -DNAMEVER='"version 1.3.3"' -DDATADIR='"/usr/share/flam3"' -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -Isrc -I.moc -I.ui -o .obj/flam3util.o src/flam3util.cpp
src/flam3util.cpp: In function ‘QTextStream& Util::operator<<(QTextStream&, flam3_frame&)’:
src/flam3util.cpp:82: error: ‘struct flam3_frame’ has no member named ‘temporal_filter_radius’
src/flam3util.cpp: In function ‘double Util::get_xform_variable(flam3_xform*, QString)’:
src/flam3util.cpp:171: error: ‘struct flam3_xform’ has no member named ‘split_xsize’
src/flam3util.cpp:172: error: ‘struct flam3_xform’ has no member named ‘split_ysize’
src/flam3util.cpp:173: error: ‘struct flam3_xform’ has no member named ‘split_shift’
src/flam3util.cpp:175: error: ‘struct flam3_xform’ has no member named ‘move_x’
src/flam3util.cpp:176: error: ‘struct flam3_xform’ has no member named ‘move_y’
src/flam3util.cpp: In function ‘void Util::set_xform_variable(flam3_xform*, QString, double)’:
src/flam3util.cpp:290: error: ‘struct flam3_xform’ has no member named ‘split_xsize’
src/flam3util.cpp:291: error: ‘struct flam3_xform’ has no member named ‘split_ysize’
src/flam3util.cpp:292: error: ‘struct flam3_xform’ has no member named ‘split_shift’
src/flam3util.cpp:294: error: ‘struct flam3_xform’ has no member named ‘move_x’
src/flam3util.cpp:295: error: ‘struct flam3_xform’ has no member named ‘move_y’
src/flam3util.cpp: In function ‘void Util::init_genome(flam3_genome*)’:
src/flam3util.cpp:461: error: ‘struct flam3_genome’ has no member named ‘motion_exp’
src/flam3util.cpp:465: error: ‘struct flam3_genome’ has no member named ‘interpolation_space’
src/flam3util.cpp:465: error: ‘flam3_intspace_linear’ was not declared in this scope
/usr/include/flam3.h: In function ‘void Util::add_default_xform(flam3_genome*)’:
/usr/include/flam3.h:389: error: too few arguments to function ‘void flam3_add_xforms(flam3_genome*, int, int)’
src/flam3util.cpp:471: error: at this point in file
make: *** [.obj/flam3util.o] Error 1
error while building qosmic
shawn@HAL:~/qosmic$ [/COLOR]

---

### Post by qamelian on 2009-06-05
Thanks. I'm not familiar with this specific app, but the methodology for compiling from source is mostly standard. I'll download the app and take a closer look at it to see if I can help.

---

### Post by albinootje on 2009-06-05
> **qamelian said:**
> Thanks. I'm not familiar with this specific app, but the methodology for compiling from source is mostly standard. I'll download the app and take a closer look at it to see if I can help.

The answer seems to be in the FAQ of the project :
[http://code.google.com/p/qosmic/wiki/BuildAndInstall](http://code.google.com/p/qosmic/wiki/BuildAndInstall)

and is ... not really standard :-)

> 
Q: I get the following error from qmake

$ qmake
Project MESSAGE: Generating Makefile for Qosmic version 1.4.2
Project MESSAGE: Qt version : 4.3.4
Project MESSAGE: Default number of rendering threads : 2
Project MESSAGE: Location of flam3-palettes.xml : /usr/local/share/flam3
Package lua was not found in the pkg-config search path.
Perhaps you should add the directory containing `lua.pc'
to the PKG_CONFIG_PATH environment variable

A: It looks like the lua-dev package didn't install the pkg-config file.

You can adjust the paths in the qosmic.pro file to point at your build dependencies. Try removing the lua entry from the PKGCONFIG variable, then try and locate lua.h somewhere in /usr/include/*, and add that directory to the INCLUDEPATH, and if liblua.so.5 is somewhere strange (other than /usr/lib) then add that path to the LIBS variable. You will also need to add '-llua' to the LIBS variable. 


---

### Post by qamelian on 2009-06-05
> **albinootje said:**
> The answer seems to be in the FAQ of the project :
[http://code.google.com/p/qosmic/wiki/BuildAndInstall](http://code.google.com/p/qosmic/wiki/BuildAndInstall)

and is ... not really standard :-)
Wonderful. Most of the time, I love installing stuff from source. Then you run into one of these oddball situations and the hair-pulling begins! :)

But that does appear to be the answer.

---

### Post by albinootje on 2009-06-05
Okay, got it compiling fine... will take a while to finish compiling, and then will I try to report back soonish with a q&d howto :)

---

### Post by albinootje on 2009-06-05
Instructions for Ubuntu Jaunty (might work on Intrepid and Hardy, YMMV) :

1) Extract the qosmic 1.4.4 source code tarball.

2) In the file qosmic.pro replace this 
```

! exists($$FLAM3_PALETTES/flam3-palettes.xml) {

```
with that :

```

! exists(/usr/local/share/flam3/flam3-palettes.xml) {

```
3) After that :
```

sudo apt-get install build-essential liblua5.1-0-dev libxml2-dev  libjpeg62-dev libpng12-dev qt4-dev-tools

```
4) Then install flam3 from source, see the README file in the qosmic directory for the url.

In case you had qt3 development files installed already, you can replace this line in build.sh (in the qosmic directory)
```

qmake || die "error while running qmake"

```
by
```

qmake-qt4 || die "error while running qmake"

```
(Or... use update-alternatives to change /etc/alternatives/qmake to make it point to qmake-qt4 instead of qmake-qt3)

5) Then follow instructions here to solve the lua problem :
[http://ubuntuforums.org/showpost.php?p=7091446&postcount=2](http://ubuntuforums.org/showpost.php?p=7091446&postcount=2)

6) Run build.sh inside the qosmic directory.

After successful compilation, run ./qosmic in the qosmic directory.

(Step 2 was probably only needed for me because I had qt3 development files installed, and I was using qmake-qt3 by mistake)

---

### Post by kd0afk on 2009-06-05
> **albinootje said:**
> The answer seems to be in the FAQ of the project :
[http://code.google.com/p/qosmic/wiki/BuildAndInstall](http://code.google.com/p/qosmic/wiki/BuildAndInstall)

and is ... not really standard :-)

Thanks. I have been trying to get someone to tell me how to add those paths and in what syntax. As soon as I know that, I will do it and see if it works.

---

### Post by qamelian on 2009-06-05
> **kd0afk said:**
> Thanks. I have been trying to get someone to tell me how to add those paths and in what syntax. As soon as I know that, I will do it and see if it works.
Usually building something from source is pretty straight-forward. Unfortunately, some projects use specialized build tools that can make thing a little more...interesting.

Hopefully, albinootje will get you on the right track with his previous post. :)

---

### Post by CylnZ on 2010-03-19
After all your sheer unpleasantness, someone helped you, and you never said a single thank you.

WTG.


Thank You! to all the folks who helped this ungrateful person. Most of us really appreciate your help :)

---

