---
title: "compiling qt"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by ettercap on 2009-03-31
Hello every 1,
I have just installed "qt-x11-opensource-src-4.4.3" , it installed find but i am unable to compile a code..
i compile it this way...(assume my file name is qt.cpp)

-> qmake -project  /* this generates a qt.pro file */
-> qmake qt.pro    /* this generates a make file */
-> make

when i execute the command make i get the below error..
this is code i try to compile
```

#include <QApplication>
#include <QLabel>
int main(int argc, char *argv[])
{
    QApplication app(argc, argv);
    QLabel *label = new QLabel("Hello Qt!");
    label->show(); 
    return app.exec();
}

```
And this is the error i get.
```

qt.cpp:1:24: error: QApplication: No such file or directory
qt.cpp:2:18: error: QLabel: No such file or directory
qt.cpp: In function ‘int main(int, char**)’:
qt.cpp:5: error: ‘QApplication’ was not declared in this scope
qt.cpp:5: error: expected `;' before ‘app’
qt.cpp:6: error: ‘QLabel’ was not declared in this scope
qt.cpp:6: error: ‘label’ was not declared in this scope
qt.cpp:6: error: expected type-specifier before ‘QLabel’
qt.cpp:6: error: expected `;' before ‘QLabel’
qt.cpp:8: error: ‘app’ was not declared in this scope
qt.cpp: At global scope:
qt.cpp:3: warning: unused parameter ‘argc’
qt.cpp:3: warning: unused parameter ‘argv’
make: *** [qt.o] Error 1

```


can any 1 plz help me out
thanks in advance !

---

### Post by KIAaze on 2009-04-02
The error is probably because you're using qt3 instead of qt4.
Here's how you can check what you are using:
```
[13][~]$  which qmake
/usr/bin/qmake
[14][~]$  readlink -f /usr/bin/qmake
/usr/bin/qmake-qt3

```

Now there are two solutions:
1)Use qt4 from the repositories
Install libqt4-dev:
```
sudo apt-get install libqt4-dev
```
Change the default qmake to qmake-qt4:
```
sudo update-alternatives --config qmake
```

Note: You can also just use "qmake-qt4" instead of "qmake" if you don't want to change the default qmake.

2)Use qt4 installed from source
You already installed it, so all you have to do is set up the paths:
```
export PATH=/usr/local/Trolltech/Qt-4.5.0/bin:$PATH
export QTDIR=/usr/local/Trolltech/Qt-4.5.0/
export LD_LIBRARY_PATH=/usr/local/Trolltech/Qt-4.5.0/lib:$LD_LIBRARY_PATH

```

---

### Post by Somnus07 on 2009-04-15
thanks KIAaze - I had the same problem; solved using the update-alternatives for qmake and changing the default to qt4  :)

---

### Post by ettercap on 2009-04-30
Amazing ! thank u very much @ KIAze

---

