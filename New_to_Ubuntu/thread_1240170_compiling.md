---
title: "compiling"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by trod on 2009-08-14
Hello I am trying to compile and install Qjoypad on my Ubuntu 64 bit computer. I am doing it this way to change the loop.cpp file to prevent the high CPU usage. I dont have experience with compiling . so far I have 1.downloaded the source code to my desktop. 
2. extracted it 
3. in the terminal I enter ./config
4. it says 

If someone wouldnt mind also telling me how I can put the terminal response in a seperated bracket like other do here it would be appreciated.

[ code ]

trod@ubuntu:~/Desktop/qjoypad-3.4.1/src$ ./config

Configuring QJoyPad installation...
------------------------------------------------------------

Device directory: /dev/input
-- Devices will be looked for in:
     /dev/input/js0
     /dev/input/js1
     etc.

Prefix directory: /usr/local
-- Files to be installed in:
     /usr/local/bin
     /usr/local/doc
     /usr/local/share/pixmaps
	 
---------------------------------------------------------
If these settings are okay, go ahead and run 'make' and
then 'make install'.

To make changes, run ./config --help for details
[ code ]

[ code ]

trod@ubuntu:~/Desktop/qjoypad-3.4.1/src$ make
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DDEVDIR='"/dev/input"' -DICON24='"/usr/local/share/pixmaps/qjoypad/icon24.png"' -DICON64='"/usr/local/share/pixmaps/qjoypad/icon64.png"' -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -Itrayicon -I/usr/share/qt3/include -o axis.o axis.cpp
In file included from axis.h:8,
                 from axis.cpp:1:
component.h:6:25: error: qstringlist.h: No such file or directory
component.h:7:25: error: qtextstream.h: No such file or directory
component.h:8:21: error: qregexp.h: No such file or directory
component.h:11:21: error: qobject.h: No such file or directory
In file included from axis.h:8,
                 from axis.cpp:1:
component.h:19: error: expected class-name before &#8216;{&#8217; token
component.h:21: error: &#8216;QTextStream&#8217; has not been declared
component.h:22: error: &#8216;QTextStream&#8217; has not been declared
component.h:27: error: &#8216;QString&#8217; does not name a type
component.h:28: error: &#8216;QString&#8217; does not name a type
In file included from axis.cpp:1:
axis.h:28: error: &#8216;QTextStream&#8217; has not been declared
axis.h:30: error: &#8216;QTextStream&#8217; has not been declared
axis.h:39: error: &#8216;QString&#8217; does not name a type
axis.h:43: error: &#8216;QString&#8217; does not name a type
axis.cpp:19: error: &#8216;bool Axis::read&#8217; is not a static member of &#8216;class Axis&#8217;
axis.cpp:19: error: &#8216;QTextStream&#8217; was not declared in this scope
axis.cpp:19: error: &#8216;stream&#8217; was not declared in this scope
axis.cpp:19: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
make: *** [axis.o] Error 1
[ code ]

---

### Post by bear24rw on 2009-08-14
did you install the qt3 dev packages?

also to do blocks to text use [+code+]stuff here[/+code+] but remove the + signs

---

### Post by trod on 2009-08-14
yes I have Qt3 development tools  installed from synaptic

---

