---
title: "Introductory C++ Class"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by Nanix on 2010-09-20
I am taking an introductory C++ computer science class online. The instructor is leaving it up to the students to find an IDE or compiler. I found Anjuta and thought it would be perfect but now I am realizing it is bloated with features only experienced programmers would understand. I have dabbled in Python on my own time with much success. I absolutely love the "python program.py" command. However it seems C++ is a lot more complicated.

In Anjuta I started a project for the first lesson: a simple "Hello World!" variant:

```
#include <iostream.h>

main()
{
    cout << "My first C++ program. \n";
    return 0;
}

```

Well, when I compiled I got some errors involving the iostream.h. I double checked with what was printed in the book and I decided that It might be due to outdated syntax (book was printed in 1998 ). I tried a modern version:
```
#include <iostream>

int main()
{
	std::cout << "Hello world!" << std::endl;
	return 0;
}
```

It compiled correctly but in doing so generated all of this stuff for a complicated program:
```
aclocal.m4      config.h.in    depcomp              ltmain.sh       NEWS
AUTHORS         config.log     INSTALL              Makefile        po
autogen.sh      config.status  install-sh           Makefile.am     README
autom4te.cache  config.sub     intltool-extract.in  Makefile.in     src
ChangeLog       configure      intltool-merge.in    missing         stamp-h1
config.guess    configure.ac   intltool-update.in   mkinstalldirs   TODO.tasks
config.h        COPYING        libtool              myfirst.anjuta

```

None of that seems necessary for a simple program...

So, I searched for a beginners Anjuta guide and could not find one. Could someone direct me to a IDE/compiler more suitable for a beginner? Or a tutorial on Anjuta for beginners? Also, to anyone experienced in C++, is 1998 material still viable in todays C++? Should I drop the class and teach myself with newer material?

---

### Post by Paul820 on 2010-09-20
Yes, you're right, Anjuta is a bit much for a beginner. I would suggest geany or codeblocks, both are in the repositories.
> sudo apt-get install geany
or
> sudo apt-get install codeblocks
Both are very easy to use.

EDIT: try and find a book that uses more up to date header files. iostream.h is not use in C++ now, they have dropped the .h extension. These are good free books [http://www.planetpdf.com/developer/article.asp?ContentID=6634]("http://www.planetpdf.com/developer/article.asp?ContentID=6634")
Or buy a copy of Accelerated C++, this is an excellent book.

---

