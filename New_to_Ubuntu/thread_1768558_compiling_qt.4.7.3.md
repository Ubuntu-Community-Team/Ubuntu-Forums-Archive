---
title: "compiling qt.4.7.3"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by manish411 on 2011-05-27
I have downloaded tar file of qt.4.7.3
and unpacked it in usr/local directory
and then:

root@utkarsh-laptop:/usr/local# 
root@utkarsh-laptop:/usr/local# cd qt-everywhere-opensource-src-4.7.3
root@utkarsh-laptop:/usr/local/qt-everywhere-opensource-src-4.7.3# 
root@utkarsh-laptop:/usr/local/qt-everywhere-opensource-src-4.7.3# ./configure
up to this everything is working  and then I am supposed to run
root@utkarsh-laptop:/usr/local/qt-everywhere-opensource-src-4.7.3# make
make: *** No targets specified and no makefile found.  Stop.
thus I cannot proceed further

---

### Post by Pand5461 on 2011-05-27
Hi!
First, do not unpack source codes to system dir! Compiling a program does not require root privileges and system dir.
So, what is the output of ./configure (specifically, the last few lines)? Does it give errors or everything is OK?

---

### Post by matt_symes on 2011-05-27
Hi

> First, do not unpack source codes to system dir! Compiling a program does not require root privileges and system dir.
So, what is the output of ./configure (specifically, the last few lines)? Does it give errors or everything is OK?

I concur. Don't unpack into a system dir. Extract to your home directory somewhere so you have no issues with permissions.

I downloaded the source tar bar myself a couple of hours ago and i have just managed to build it by using the standard ./configure and make.

What were the exact instructions you ran ?

Kind regards

Kind regards

---

### Post by manish411 on 2011-05-27
I am reading the book "beginning linux programming" and I am following the instructions ::

The source package comes with exten-
sive instructions on how to compile and install Qt in the INSTALL file in the tarred package:
$cd /usr/local
$tar &#8211;xvzf qt-x11-free-3.3.8.tar.gz
$./configure
$make
You&#8217;ll also need to add a line to /etc/ld.so.conf:
/usr/lib/qt-3.3/lib
When Qt is properly installed, the QTDIR environment variable should be set to the Qt installation direc-
tory. You can check that this is the case as follows:
$ echo $QTDIR
/usr/lib/qt-3.3
Also make sure the lib directory is added to /etc/ld.so.conf.
Then run the following command as superuser:
# ldconfig

---

### Post by Pand5461 on 2011-05-27
So you just want to install _some_ version of Qt? Then you'd better install libqt4-dev via Software centre or Synaptic.

---

### Post by manish411 on 2011-05-27
but what difference does it make as long as I am able to run programs and create applications

---

### Post by Pand5461 on 2011-05-27
First, it's easier. But more important is that with installation from repository all parameters (such as environment variables etc.) are set correctly and automatically.
When you install a package from repos you may be sure that it's installed properly and won't cause problems on upgrade or installing other packages.

---

### Post by manish411 on 2011-05-28
that means you are able to run the applications you make . Can you please give me the link from where exactly you downloaded the binary and elaborate step by step the installation process.

---

### Post by Pand5461 on 2011-05-28
You can either install libqt4-dev via Synaptic (System > Administration > Synaptic Package Manager) or via APT
```
sudo apt-get install libqt4-dev
```

---

### Post by manish411 on 2011-05-28
ok so I installed it.
then I make a file
/code:
#include <qapplication.h>
#include <qmainwindow.h>
int main(int argc, char **argv)
{
QApplication app(argc, argv);
QMainWindow *window = new QMainWindow();
app.setMainWidget(window);
window->show();
return app.exec();
}/code
and run it according to the book
umahar@utkarsh-laptop:~/programming/qt$ g++ -o qt1 qt1.cpp -I$QTDIR/include -L$QTDIR/lib -lquiqt1.cpp:1:26: error: qapplication.h: No such file or directory
qt1.cpp:2:25: error: qmainwindow.h: No such file or directory
qt1.cpp: In function &#8216;int main(int, char**)&#8217;:
qt1.cpp:5: error: &#8216;QApplication&#8217; was not declared in this scope
qt1.cpp:5: error: expected &#8216;;&#8217; before &#8216;app&#8217;
qt1.cpp:6: error: &#8216;QMainWindow&#8217; was not declared in this scope
qt1.cpp:6: error: &#8216;window&#8217; was not declared in this scope
qt1.cpp:6: error: expected type-specifier before &#8216;QMainWindow&#8217;
qt1.cpp:6: error: expected &#8216;;&#8217; before &#8216;QMainWindow&#8217;
qt1.cpp:7: error: &#8216;app&#8217; was not declared in this scope
but it gives these errors

---

### Post by benson444 on 2011-05-28
The book you're reading is for Qt3. Qt4 can be significantly different. You can download the first edition of "C++ GUI Programming With Qt4" for free from [http://www.qtrac.eu/marksummerfield.html]("http://www.qtrac.eu/marksummerfield.html")

As for the code you have, I would say

Change the #includes to <QApplication> and <QMainWindow>

Remove/comment the line "app.setMainWidget(window);". Method is not in Qt4.

Place the file in an empty directory, cd to it and compile with:

```
qmake -project
qmake
make
```

---

### Post by myfeing on 2011-06-09
> **manish411 said:**
> I have downloaded tar file of qt.4.7.3
and unpacked it in usr/local directory
and then:

root@utkarsh-laptop:/usr/local# 
root@utkarsh-laptop:/usr/local# cd qt-everywhere-opensource-src-4.7.3
root@utkarsh-laptop:/usr/local/qt-everywhere-opensource-src-4.7.3# 
root@utkarsh-laptop:/usr/local/qt-everywhere-opensource-src-4.7.3# ./configure
up to this everything is working  and then I am supposed to run
root@utkarsh-laptop:/usr/local/qt-everywhere-opensource-src-4.7.3# make
make: *** No targets specified and no makefile found.  Stop.
thus I cannot proceed further

i checked the package "qt-everywhere-opensource-src-4.7.3.tar.gz", it doesnt contain a "Makefile" like other source code package.

./configure only generate the qmake files which in the "qmake" subdirectory.

is only libqt4-dev.so necessary to run the make && make install? i will try it.

---

