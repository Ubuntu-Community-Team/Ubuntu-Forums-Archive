---
title: "How to install software without ./configure?"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by DzmitryG on 2010-03-03
I want to run a program called [GENtle]("http://gentle.magnusmanske.de/GENtle.tar.gz") and I have no idea how to install it. There is no configure file in the directory. This is a great piece of biosoftware from Magnus Manske which is comparable with VectorNTI and I had it running well from Windows and from Linux in Wine. Now I have to use PPC and the only program that is available from Ubuntu ports is Ugene which is absolutely impossible to to use after GENtle.
I would really appreciate if someone could guide me to any sort of info about this or any hint.

Ideally, of course, would be nice to build a package that one could just apt-get, but it is only a dream aloud )

---

### Post by Alexandre Putt on 2010-03-03
What does the documentation for it say? If there is no configure, is there a makefile?

---

### Post by Jefferythewind on 2010-03-03
That looks like a cool tool.  I looked at the website, and since I am not on my home computer I can only say to install the prerequisite packages mentioned on the website, and then try to compile the software from the packages. 

```
./configure

make

sudo make install

clean install
```

---

### Post by DzmitryG on 2010-03-03
In the archive there is an executable file, but if I double click it - nothing happens. There are a few .csv files and a .tab file + two directories (help and bitmaps).

---

### Post by undecim on 2010-03-03
The tar.gz  is a binary download, not a source download.

Just install the packages named on the home page and you should be able to run the GENtle file from the directory you exctracted to.

If that give you issues (i'm having trouble, but I think that's becuase I'm on a 64-bit machine, so it's not finding the 32-bit libraries it wants), you can install from source from the CVS repo as explained [here]("http://sourceforge.net/scm/?type=cvs&group_id=89980")

---

### Post by nothingspecial on 2010-03-03
Also it looks for libmysqlclient-14 but karmic only has 15 and 16 so you are going to have to solve that too.

---

### Post by DzmitryG on 2010-03-03
Sounds so easy ) I hope I did post it under **Absolute Beginner Talk**.
I guess there is no simple way to do this. As I mentioned, I need to run it on PPC, and it does not run if I double click (or "sudo open" it). Compiling a new one for me is something high above the sky. But, anyway, thanks for explaining.

---

### Post by Alexandre Putt on 2010-03-03
> **DzmitryG said:**
> Sounds so easy ) I hope I did post it under **Absolute Beginner Talk**.
I guess there is no simple way to do this. As I mentioned, I need to run it on PPC, and it does not run if I double click (or "sudo open" it). Compiling a new one for me is something high above the sky. But, anyway, thanks for explaining.

If the architecture is different, then the binary is useless. Compiling from source is a piece of cake. You do not need to know anything about programming to do it. So give it a try.

---

### Post by DzmitryG on 2010-03-04
I am trying now, following this [HOWTO]("http://ubuntuforums.org/showthread.php?t=323939"). And it is not that easy for me. I have a number of questions I'd be happy if anyone answers:

1) Is it possible/easier to compile from the 3 libraries provided (libmysqlclient.so.12, libsqlite.so.0 and libsqlite3.so.0) as source code or it has to be this CVS thingy?

2) Assuming it has to be CVS, what do I write as a modulname in these promts: 
```
cvs -d:pserver:anonymous@gentle-m.cvs.sourceforge.net:/cvsroot/gentle-m login             
cvs -z3 -d:pserver:anonymous@gentle-m.cvs.sourceforge.net:/cvsroot/gentle-m co -P *modulename*
```The web-based repositary viewer is [here]("http://gentle-m.cvs.sourceforge.net/viewvc/gentle-m/GENtle/").

3) And regarding libmysqlclient14  - do I simply search for and install this particular version or the source code should be changed? 

4) And finally, which options I compile with???

Thanks!

---

### Post by Alexandre Putt on 2010-03-05
> **DzmitryG said:**
> 
1) Is it possible/easier to compile from the 3 libraries provided (libmysqlclient.so.12, libsqlite.so.0 and libsqlite3.so.0) as source code or it has to be this CVS thingy?

Installing -dev versions if these packages from the repository should be sufficient. The same applies to other mentioned libraries. If you don't find any, look for more general development packages for sqlite.

Usually you do not need additional options for compiling. There should be a configuration file in the source which sets the options for you.

---

### Post by Alexandre Putt on 2010-03-05
The readme file from here

[http://gentle-m.cvs.sourceforge.net/viewvc/gentle-m/GENtle/README.Ubuntu?revision=1.2&view=markup](http://gentle-m.cvs.sourceforge.net/viewvc/gentle-m/GENtle/README.Ubuntu?revision=1.2&view=markup)

says:

 To compile on Ubuntu (tested on Hairy Hadron, or something),
    2 sudo apt-get install the following packages:
    3 libwxgtk2.8-dev
    4 automake1.9
    5 libmysql++-dev
    6 libsqlite0-dev
    7 libsqlite3-dev
    8 
    9 Then the usual
   10 ./configure
   11 make
   12 
   13 Done!
   14 
   15 If anyone could make a decent package from GENtle, or better help me make one,

There is a direct link to a file GENtle libraries with source code, but I am not sure if this is what you are looking for:

[http://sourceforge.net/projects/gentle-m/files/Linux%20support%20libraries/MySQL%20client%20and%20sqlite%202.8%20libraries/GENtle_libraries.tar.bz2/download](http://sourceforge.net/projects/gentle-m/files/Linux%20support%20libraries/MySQL%20client%20and%20sqlite%202.8%20libraries/GENtle_libraries.tar.bz2/download)

---

### Post by DzmitryG on 2010-03-05
Thanks! I did not have the tools. However now I can't connect to the repository: after I put ```
cvs -z3 -d:pserver:anonymous@gentle-m.cvs.sourceforge.net:/cvsroot/gentle-m co -P GENtle
``` (being logged in), it says "cvs checkout: cannot open CVS/Entries for reading: No such file or directory
cvs [checkout aborted]: no repository". Also yesterday when I was entering the same, it did not give such thing. I still see the repository with web-based viewer, and not from my cash. Why is it changed?

---

### Post by Alexandre Putt on 2010-03-05
Isn't the link I gave pointing to the same files as in cvs? Sorry, I am not familiar with cvs at all. 

But if the link gives you the same bundle, you don't need to use cvs. Just unpack the content and ./configure and make it. 

If this is different, then sorry, you'll need to read on cvs to figure it out.

---

### Post by DzmitryG on 2010-03-05
No, in the archive there are only 3 files, without configure or anything. I guess it must be CVS. I also asked our Linux guru in the center to help with compiling, and he could not do it straight away - there is a problem with one of the libraries. Meanwhile, I am trying to dig it for myself, and thanks for the advises.

---

### Post by Alexandre Putt on 2010-03-05
Sorry, I was browsing the file list and thought the link pointed to it. Anyway, I am able to retrieve the files with the second csv command without a problem. Does it work for you now? Did you get the files? ./configure should guide through the rest.

---

### Post by nothingspecial on 2010-03-05
Well I installed libmysqlclient-14 alongside libmysqlclient-16 and GENtle ran.

Not sure if that is a good idea, I wouldn`t have thought so.

You`re still going to have to build it for PPC though.

---

### Post by DzmitryG on 2010-03-06
On home PC, while running ./configure, get this:

dzmitry@mubuntu:~/GENtle$ ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
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


I have all the mentioned in the topic packages installed. What's missing here?

---

### Post by nothingspecial on 2010-03-06
You need a compiler

```
sudo apt-get install build-essential
```

Then try again

---

### Post by DzmitryG on 2010-03-06
Oops, true. Forgot this. And here comes the "bad" library:

o" -c -o ureadseq.o ureadseq.c; \
    then mv -f ".deps/ureadseq.Tpo" ".deps/ureadseq.Po"; else rm -f ".deps/ureadseq.Tpo"; exit 1; fi
ureadseq.c:141: error: conflicting types for ‘getline’
/usr/include/stdio.h:651: note: previous declaration of ‘getline’ was here
ureadseq.c: In function ‘seqFileFormatFp’:
ureadseq.c:1347: warning: format ‘%d’ expects type ‘int *’, but argument 3 has type ‘long int *’
ureadseq.c:1347: warning: format ‘%d’ expects type ‘int *’, but argument 4 has type ‘long int *’
ureadseq.c: In function ‘writeSeq’:
ureadseq.c:1593: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long int’
ureadseq.c:1622: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long int’
ureadseq.c:1623: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long int’
ureadseq.c:1623: warning: format ‘%X’ expects type ‘unsigned int’, but argument 5 has type ‘long unsigned int’
ureadseq.c:1637: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long int’
ureadseq.c:1637: warning: format ‘%X’ expects type ‘unsigned int’, but argument 5 has type ‘long unsigned int’
ureadseq.c:1647: warning: format ‘%10d’ expects type ‘int’, but argument 3 has type ‘long int’
ureadseq.c:1657: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long int’
ureadseq.c:1657: warning: format ‘%X’ expects type ‘unsigned int’, but argument 5 has type ‘long unsigned int’
ureadseq.c:1666: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long int’
ureadseq.c:1666: warning: format ‘%X’ expects type ‘unsigned int’, but argument 5 has type ‘long unsigned int’
ureadseq.c:1667: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long int’
ureadseq.c:1678: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long int’
ureadseq.c:1678: warning: format ‘%d’ expects type ‘int’, but argument 5 has type ‘long unsigned int’
ureadseq.c:1687: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long int’
ureadseq.c:1687: warning: format ‘%X’ expects type ‘unsigned int’, but argument 5 has type ‘long unsigned int’
ureadseq.c:1693: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long int’
ureadseq.c:1693: warning: format ‘%X’ expects type ‘unsigned int’, but argument 5 has type ‘long unsigned int’
ureadseq.c:1724: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long int’
ureadseq.c:1746: warning: format ‘%6d’ expects type ‘int’, but argument 4 has type ‘long int’
ureadseq.c:1746: warning: format ‘%8X’ expects type ‘unsigned int’, but argument 5 has type ‘long unsigned int’
ureadseq.c:1763: warning: format ‘%6d’ expects type ‘int’, but argument 4 has type ‘long int’
ureadseq.c:1763: warning: format ‘%8X’ expects type ‘unsigned int’, but argument 5 has type ‘long unsigned int’
ureadseq.c:1770: warning: format ‘%6d’ expects type ‘int’, but argument 4 has type ‘long int’
ureadseq.c:1770: warning: format ‘%5d’ expects type ‘int’, but argument 5 has type ‘long unsigned int’
ureadseq.c:1781: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long int’
ureadseq.c:1781: warning: format ‘%X’ expects type ‘unsigned int’, but argument 5 has type ‘long unsigned int’
ureadseq.c:1790: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long int’
ureadseq.c:1790: warning: format ‘%X’ expects type ‘unsigned int’, but argument 5 has type ‘long unsigned int’
ureadseq.c:1831: warning: format ‘%-9d’ expects type ‘int’, but argument 3 has type ‘long int’
make: *** [ureadseq.o] Error 1


(((

---

### Post by DzmitryG on 2010-03-06
Anyway, I guess it is outside of the topic. To summarize Compiling GENtle From Source Code:
1) ```
sudo apt-get install build-essential libwxgtk2.8-dev automake1.9 libmysql++-dev libsqlite0-dev libsqlite3-dev libsqlite0 libsqlite3-0 libwxgtk2.6-0
```2) download and install [libmysqclient-14]("http://packages.ubuntu.com/dapper/libmysqlclient14")
3) connect to the repository:
```
cvs -d:pserver:anonymous@gentle-m.cvs.sourceforge.net:/cvsroot/gentle-m login             
*ENTER*
cvs -z3 -d:pserver:anonymous@gentle-m.cvs.sourceforge.net:/cvsroot/gentle-m co -P GENtle
```4) change directory
```
cd GENtle
```5) do usual
```
./configure
make
make install
```and keep fingers crossed not to get error in ureadseq

**Moderators**, please, change the topic of the thread.

---

### Post by nothingspecial on 2010-03-06
So is it working?

Also if it is not, and I notice you are trying this on your home pc. You just need to download the tarball, install libmysqclient-14 and ./GENtle

I have no idea weather it works properly, I couldn`t tell a gene from a joystick.

---

### Post by DzmitryG on 2010-03-06
It is working on PC (32) from this [binary]("http://gentle.magnusmanske.de/GENtle.tar.gz") if you install libmysqlclient-14 (thanks! at least I can try Linux version). But it does not compile - gives this error in ureadseq.c. Maybe one needs old compiling programs in order to do so. Should I try to find older versions of packages from build-essential? Or is it more wxGTK-dev? I mean, somebody obviously was able to compile it before (I guess, Magnus Manske himself).

---

### Post by nothingspecial on 2010-03-06
No, the compilers aren`t the problem.

Unfortunately, without a PPC, I don`t know what is.

---

### Post by DzmitryG on 2010-03-06
It can't be compiled *de novo* on PC either.

---

### Post by DzmitryG on 2010-03-08
Thanks to gmargo, the issue with the ureadseq.c can be [fixed]("http://ubuntuforums.org/showthread.php?p=8932364#post8932364") now. Appeared to be a conflict of GENtle's "getline" with Karmic "getline". I have successfully compiled GENtle on 32-bit Karmic Koala and powerpc Karmic Koala. Here is the protocol:

1. Install the packages:```
sudo apt-get install build-essential libwxgtk2.8-dev automake1.9 libmysql++-dev libsqlite0-dev libsqlite3-dev libmysqlclient14 libsqlite0 libsqlite3-0 libwxgtk2.6-0 cvs
```[URL="http://http://packages.ubuntu.com/dapper/libmysqlclient14"]
[/URL]2. Connect to CVS repo:```
cvs -d:pserver:anonymous@gentle-m.cvs.sourceforge.net:/cvsroot/gentle-m login
```press ENTER when asked for password
3. The following command will download source files from the repo onto your hard-drive, into the folder you have opened terminal in (default - /home/*user_name*)```
cvs -z3 -d:pserver:anonymous@gentle-m.cvs.sourceforge.net:/cvsroot/gentle-m co -P GENtle
```4. Change directory:```
cd GENtle
```5. Open ureadseq.c file in your favorite text editor and replace all the "getline" with "getline_gentle". Save it.
6. In terminal:```
./configure
sudo make
```Next should be "sudo make install" and "sudo make clean install", but GENtle will not run properly from the /usr/bin directory. I just copied files below into a different folder and run GENtle by double click on executable.

/bitmaps   codon_catalog.csv  default.tab  /help      tips_en.txt
blank.db  commonvectors.db   GENtle       local.db  variables.csv

---

