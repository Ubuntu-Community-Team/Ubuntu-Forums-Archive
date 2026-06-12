---
title: "C++ compiler"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by art_monu on 2010-10-18
Hello,
I am a beginner in Ubuntu. I want to learn C++. I have been using Turbo c++ in windows for running C++ programs. I searched for Ubuntu and installed gcc. But I do not see gcc anywhere and I can not open it. After searching again I found something that I will have to write the whole program first in .txt format and then run it using terminal. But I do not want to go for terminal every time as I don't know anything about it.
        Please suggest me just one C++ compiler similar to Turbo C++ which I can open like a program as it is in windows so that I will not have to go to terminal. Also tell me step by step how to install it and open it.
  I use Ubuntu 10.04 LTS desktop edition.
Please help!

---

### Post by JackNocturne on 2010-10-18
Hello,
Its simple to use IDE interface, download the following programs from Ubuntu **software-center**


[LIST]
[*]Anjuta IDE
[*]Monodevelop
[/LIST]
Try them,they both do the same thing. In time delete the one you don't use. Cheers.

---

### Post by blueabysm on 2010-10-18
GCC is not a visualized editor or IDE, it is just a compiler. you can use vi to edit your code and use gcc to compile your code by following these steps:

Open terminal and type the command below to create a c source file named test.c
```
vi test.c
```

Then press i, and type your code.
after you finish it, press button Esc, and type ':wq' to save and exit.

then you have returned to terminal. type the commands below to compile and run your code. (Suppose that you name your application "test"
```

gcc ./test.c -o ./test
test

```


Of course, an IDE will be a better choice. Such as Anjuta IDE and so on.

---

### Post by Paul820 on 2010-10-18
> sudo apt-get install codeblocks

Very easy to use IDE for C/C++ programming.

---

### Post by srs5694 on 2010-10-18
To provide necessary background: IDE in this context stands for "integrated development environment." This is a set of tools to assist in software development -- mainly a programming editor and GUI front-ends to text-mode tools such as gcc and g++. The Windows Turbo C++ software package is an IDE and compiler sold in one box. In Linux, these elements are unbundled, so you install the GCC package and then either use it "raw" or pick an IDE to use. JackNocturne mentioned a couple. There's also Code::Blocks, KDevelop, and probably others. (FWIW, I use KDevelop.)

---

### Post by anewguy on 2010-10-18
Also, if you just installed gcc and g++, I'd recommend you install the package "build-essential".  Not being familiar enough with the various packages mentioned for IDE's, one thing I don't know is if they have the debugger where you can step in, watch variables, etc., integrated as well.  Someone else would have to tell you that.

Dave ;)

---

