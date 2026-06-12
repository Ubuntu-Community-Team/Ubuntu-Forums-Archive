---
title: "c/c++ compiler"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by nadav reichler on 2010-11-05
I'm looking for a c/c++ compiler. which one is the best to start with?
(I tried to use g++-4.4 but I couldn't figure out how it works)

---

### Post by Paul820 on 2010-11-05
gcc/g++ is the standard compiler on Ubuntu. Why are you having trouble with it? To compile this on the command line:
> #include <iostream>

int main()
{
    std::cout << "Hello World" << std::endl;
    
    return 0;
}

Enter this in the terminal

> g++ -o test test.cpp

Which will produce a file called **test**, to run the program enter

> ./test

in the terminal. Assuming you are in the correct path.

If you don't want to compile from the command line, download **geany** from synaptic, it's a very lightweight IDE. If you want something a bit more powerful, download **codeblocks**, again through synaptic. If you want something more powerful than codeblocks, download **Anjuta**.

If you do decide to build from the command line, i would suggest you get **nautilus-open-terminal**, it allows you to open a terminal anywhere. Just right click and choose O**pen In Terminal**. Saves writing the whole path every time. :)

---

### Post by nadav reichler on 2010-11-05
first of all thanks for your help.
I tried what you wrote an this is what happened:

[http://yfrog.com/f/ccghelpp/](http://yfrog.com/f/ccghelpp/)

what I understood is that I didn't install g++ but I did.

---

### Post by Paul820 on 2010-11-05
Open a terminal and copy and paste this:
> sudo apt-get install build-essential

EDIT: Then compile again.

---

### Post by yancouto on 2010-11-05
I like using codeblocks to write in c.
Try it, just download it at the software center.

---

### Post by anewguy on 2010-11-05
Indeed, build-essential will install the compilers and other things you may need when compiling.  And as noted above, remember that they are JUST compilers - not Integrated Development Environment(s) such a Visual C, Visual C++, Visual Basic, etc..  There are other tools in Linux which can be used in a similar fashion, but you must install build-essential first.

Dave ;)

---

### Post by GregBrannon on 2010-11-05
Stop by Programming Talk (jump to forums at the bottom of most pages, near the bottom of a LOOOONG list), read the stickies, threads, etc. to learn more about C++ programming, IDEs, or whatever else you want to do with programming.

---

