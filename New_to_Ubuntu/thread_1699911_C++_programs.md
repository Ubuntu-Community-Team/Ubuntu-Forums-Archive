---
title: "C++ programs"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by abnordude on 2011-03-04
Well.
I'm quite new to ubuntu.
I've been in xp for a long time. 
I did my c++ programs in turbo c++
Now switched completely to ubuntu. And I totally love it more than windows. 
But I don't know how to do my c++ programming.
I need a software [in ubuntu] to do my c++ programming.
I hate the use of wine so please dont suggest me that.

---

### Post by turtle153 on 2011-03-04
You need the GNU C Compiler (gcc) for Linux. [https://help.ubuntu.com/community/InstallingCompilers](https://help.ubuntu.com/community/InstallingCompilers)

It's a command line compiler so you can write the program in a standard text editor.

---

### Post by maqtanim on 2011-03-04
First install the **build essential** by running the following command in the terminal
```
sudo apt-get install build-essential
```

Then install **Code Blocks** from the Ubuntu Software Center.

Now you'll found a new sub-menu named programming, under Applications menu on the top panel. Go there and click the Code Blocks there. You can do your C++ programming from here! :)

---

### Post by turtle153 on 2011-03-04
Ahhh code::blocks, one hell of an ugly program :p

---

### Post by vivek.pandey on 2011-03-04
well instead of any software i prefer  this...use a text editor eg gedit...write your codes and save it as .cpp or .c++...for c++ you need a compiler g++.. you can install it using termainal go to terminal and type g++ you will be shown a list of g++ packages choose one and then sudo apt-get install package name

to compile and run any program
g++ filename if the file is in home directory else g++ filepath
to run you can use ./a.out
thats it...easy huh? :-)

---

### Post by abnordude on 2011-03-04
> **turtle153 said:**
> You need the GNU C Compiler (gcc) for Linux. [https://help.ubuntu.com/community/InstallingCompilers](https://help.ubuntu.com/community/InstallingCompilers)

It's a command line compiler so you can write the program in a standard text editor.

Can you tell me more about this gcc.
about how to install and how to start doing programming.

---

### Post by vivek.pandey on 2011-03-04
for c++ you need g++ and not gcc...gcc is for c

---

### Post by abnordude on 2011-03-04
> **neo_aryan said:**
> for c++ you need g++ and not gcc...gcc is for c

I think i hav the g++ installed, but then how to start it?
how to write programs?

---

### Post by abnordude on 2011-03-04
> **maqtanim said:**
> First install the **build essential** by running the following command in the terminal
```
sudo apt-get install build-essential
```Then install **Code Blocks** from the Ubuntu Software Center.

Now you'll found a new sub-menu named programming, under Applications menu on the top panel. Go there and click the Code Blocks there. You can do your C++ programming from here! :)


I downloaded code blocks just like you said. But I find it very complicated.
Hence, I was seeing if g++ could help me.

---

### Post by turtle153 on 2011-03-04
[http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html](http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html)

---

### Post by vivek.pandey on 2011-03-04
> **abnordude said:**
> I think i hav the g++ installed, but then how to start it?
how to write programs?

the method is same as you right in turbo only thing is you need to include a line after including header files and that is using namespace std;

about compilation and runing i have written in the previous post just look in your thread

---

### Post by abnordude on 2011-03-04
> **turtle153 said:**
> [http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html](http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html)

Sorry, I'm quite new to this, and hence i didnt understand the details given in the link.
Is there any video tutorials on how to do this?

---

### Post by abnordude on 2011-03-04
> **neo_aryan said:**
> well instead of any software i prefer  this...use a text editor eg gedit...write your codes and save it as .cpp or .c++...for c++ you need a compiler g++.. you can install it using termainal go to terminal and type g++ you will be shown a list of g++ packages choose one and then sudo apt-get install package name

to compile and run any program
g++ filename if the file is in home directory else g++ filepath
to run you can use ./a.out
thats it...easy huh? :-)

Could you exaggerate.
I mean, where should we type " ./a.out" etc.
Sorry, i'm new to this.

---

### Post by turtle153 on 2011-03-04
Ah. Go to Applications > Accessories > Terminal and enter it all into that, one line at a time.

---

### Post by vivek.pandey on 2011-03-04
> **abnordude said:**
> Could you exaggerate.
I mean, where should we type " ./a.out" etc.
Sorry, i'm new to this.

k here is a sample hello world program
#include <iostream>
using namespace std;
int main()
{
  cout<<"hello world"<<endl;
  }
write this code in a text editor say gedit..you can get it here
applications ->accessories->gedit
save it as hello.cpp or hello.c++..you can do that by ctrl+s or save option in the window.. to start off i would say better save it in your home folder
next go to terminal
type
g++ hello.cpp
this compiles your program
then run it by typing
./a.out 
in the terminal
you will get the output as 
hello world

hope this helped
t

---

### Post by maqtanim on 2011-03-04
> **abnordude said:**
> I downloaded code blocks just like you said. But I find it very complicated.
Hence, I was seeing if g++ could help me.
CodeBlock is an [IDE]("http://en.wikipedia.org/wiki/Integrated_development_environment") for writing programs (and it is for new programmers actually). Try the following links for a handy manual of CodeBlocks.
[http://www.sci.brooklyn.cuny.edu/~parsons/courses/15-fall-2008/notes/howto-codeblocks.pdf](http://www.sci.brooklyn.cuny.edu/~parsons/courses/15-fall-2008/notes/howto-codeblocks.pdf)
[http://www.sci.brooklyn.cuny.edu/~goetz/codeblocks/codeblocks-instructions.pdf](http://www.sci.brooklyn.cuny.edu/~goetz/codeblocks/codeblocks-instructions.pdf)

---

### Post by abnordude on 2011-03-04
> **neo_aryan said:**
> k here is a sample hello world program
#include <iostream>
using namespace std;
int main()
{
  cout<<"hello world"<<endl;
  }
write this code in a text editor say gedit..you can get it here
applications ->accessories->gedit
save it as hello.cpp or hello.c++..you can do that by ctrl+s or save option in the window.. to start off i would say better save it in your home folder
next go to terminal
type
g++ hello.cpp
this compiles your program
then run it by typing
./a.out 
in the terminal
you will get the output as 
hello world

hope this helped
t

Thanks very much. It worked.
That's nice.
Thanks to all those who have helped me.

---

### Post by abnordude on 2012-07-04
I know many months have passed since this post...and I just wanted to say that I'm currently doing c++ programming in an IDE (i prefer an IDE to the command line) called Geany...(ofcourse one needs the handy g++ compiler to do so)

Hope it helps...................

---

### Post by nll on 2012-07-04
Hey, try Qt Creator someday, it's great! There are some video tutorials here: [http://www.youtube.com/user/VoidRealms](http://www.youtube.com/user/VoidRealms)

---

### Post by abnordude on 2012-07-06
> **nll said:**
> Hey, try Qt Creator someday, it's great! There are some video tutorials here: [http://www.youtube.com/user/VoidRealms](http://www.youtube.com/user/VoidRealms)

Thanks for the suggestion.....
I will definitely give a hand at it....

---

### Post by anewguy on 2012-07-06
Also, for anyone just starting out, use of gcc or g++ from the command line usually requires more than the simple example given in this thread.  Additional libraries, etc., are often required and need to be added to statement so the linker can grab them.  Sometimes the use of pkg-config is needed.

---

