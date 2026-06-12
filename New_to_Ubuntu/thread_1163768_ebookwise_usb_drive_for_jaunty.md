---
title: "ebookwise usb drive for jaunty"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by orwellus on 2009-05-19
Hello

I got an ebookwise 1150 today, and it works fine on Windows XP, but I'm having trouble installing the drive for ubuntu jaunty.

I went to this site:

[http://www.mobileread.mobi/forums/showthread.php?t=35960](http://www.mobileread.mobi/forums/showthread.php?t=35960)

and installed the latest ebookwise usb drive, and added the #include <string.h> correction via the sudo gedit. When I do ./configure ,in the terminal, everything seems to be okay, but when I try make I get the following error:

make  all-recursive
make[1]: Entering directory `/home/kmlogue/Desktop/eb1150-0.1.1'
Making all in src
make[2]: Entering directory `/home/kmlogue/Desktop/eb1150-0.1.1/src'
g++ -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.cpp
main.cpp: In function ‘int main(int, char**)’:
main.cpp:33: warning: deprecated conversion from string constant to ‘char*’
mv -f .deps/main.Tpo .deps/main.Po
g++ -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT dev1150.o -MD -MP -MF .deps/dev1150.Tpo -c -o dev1150.o dev1150.cpp
In file included from dev1150.cpp:16:
dev1150.h:31: error: ‘std::string’ has not been declared
dev1150.h:32: error: ‘std::string’ has not been declared
dev1150.cpp:81: error: prototype for ‘void Dev1150::read(std::string&)’ does not match any in class ‘Dev1150’
dev1150.h:31: error: candidate is: void Dev1150::read(int&)
dev1150.cpp:94: error: prototype for ‘void Dev1150::write(std::string)’ does not match any in class ‘Dev1150’
dev1150.h:32: error: candidate is: void Dev1150::write(int)
make[2]: *** [dev1150.o] Error 1
make[2]: Leaving directory `/home/kmlogue/Desktop/eb1150-0.1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kmlogue/Desktop/eb1150-0.1.1'
make: *** [all] Error 2

Any suggestions? Is it because I have Jaunty, and there isn't an ebookwise usb drive for Jaunty yet?

---

### Post by orwellus on 2009-05-23
Okay, I got this to work for Jaunty. I'll try to explain how I did it. 

Download the drive from here

[http://www.mobileread.com/forums/attachment.php?attachmentid=15545](http://www.mobileread.com/forums/attachment.php?attachmentid=15545) d=1219574808

Extract the file (right click, and select extract here)

Open the eb1150-0.1.1 folder. Now open the src folder.

Open the following three files:

dev1150.cpp
dev1150.h
main.cpp

add the line:

#include <string.h>

In with the other #include lines.

Save, and exit files and the eb1150-0.1.1 folder. 

Move (or cut and paste) the eb1150-0.1.1 folder to your home folder. Open a terminal, and change into the eb1150-0.1.1 folder (cd eb1150-0.1.1)

Then

./configure
make
sudo make install

Hopefully there are no errors. When that's done. You should be able to turn on your ebookwise, plug in the usb, and open the drive in a terminal using the command:

sudo eb1150

Alternatively, you can follow the directions on this guy's site:

[http://www.mobileread.mobi/forums/showthread.php?t=28166](http://www.mobileread.mobi/forums/showthread.php?t=28166)

---

### Post by Ron O on 2009-05-31
I have a different problem with eb1150 and I hope someone can figure this one out. I am using Jaunty (Xubuntu) with the libusb and libusb-dev 0.1-4 version 2:0.1.12-3 and when I went to configure/make eb1150 I got errors. 

I then added from Synaptic 1.0-0 ver 2:1.0.0-1 (keeping the newer ones as well) and the C++ USB programming libraries libusb++ and dev 0.1-4c2 ver 2:0.1.12-13. Same errors. Terminal output:

rpo@ronouel:~/eb1150-0.1.1$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details. 

I can add the config log if this is not enough.

I cannot figure this out- could it be a permissions problem? I'd love to get content on my book reader without going to a personal content server in Windoze which I visit very rarely now. But it happens that the Windoze USB driver is all I have that works.

---

### Post by Ron O on 2009-06-12
It was the G++ package that was missing, which is the GNU version of C++.
I started by installing that one and it worked fine.

---

