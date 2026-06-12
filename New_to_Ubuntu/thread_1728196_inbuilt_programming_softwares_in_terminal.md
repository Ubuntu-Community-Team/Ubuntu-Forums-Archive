---
title: "inbuilt programming softwares in terminal ?"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by naved ..... on 2011-04-13
i  heard that ubuntu terminal has all programming software like c,  c++,java , perl , python , asp.net , etc inbuilt ????? ..so we dont need  to install extra software for the same , like in windows we have to  install different software for different programming lanuguage ...i m  using ubuntu (linux) just for programming bcoz i m a programmer and i  need to do a lot of  programming stuff !! plz also reply 4 this pzl help  !!!

---

### Post by rosencrantz on 2011-04-13
double post.

---

### Post by Nytram on 2011-04-13
As far as I know these languages are installed by default:

C/C++ Python Mono Shell-script

You'll need to manually install the others.

---

### Post by vivek.pandey on 2011-04-13
> **naved ..... said:**
> i  heard that ubuntu terminal has all programming software like c,  c++,java , perl , python , asp.net , etc inbuilt ????? ..so we dont need  to install extra software for the same , like in windows we have to  install different software for different programming lanuguage ...i m  using ubuntu (linux) just for programming bcoz i m a programmer and i  need to do a lot of  programming stuff !! plz also reply 4 this pzl help  !!!

python interpretter and gcc (c compiler) are installed. i guess perl is also installed . o know whether its installed or not type on terminal perl you will get to know 
to install c++ compiler
on your terminal write g++  you will get  a list of packages
then type

```
sudo apt-get install packagename 
```
same for java ype javac on terminal you will again get a list of packages
```
 sudo apt-get install packagename 
```

---

### Post by directhex on 2011-04-13
> **naved ..... said:**
> i  heard that ubuntu terminal has all programming software like c,  c++,java , perl , python , asp.net , etc inbuilt ????? ..so we dont need  to install extra software for the same , like in windows we have to  install different software for different programming lanuguage ...i m  using ubuntu (linux) just for programming bcoz i m a programmer and i  need to do a lot of  programming stuff !! plz also reply 4 this pzl help  !!!

The compilers for all of these are not installed by default. Some support for apps written with them may be installed. In the case of scripting languages like Perl, those are the same thing - but for compiled languages, you need to install the compiler package.

---

### Post by earthpigg on 2011-04-13
here, i'll give you a practical example that should clear up some of the theoretical confusion:

```
nano test.py
```

enter these two lines in the text file:
```

#! /usr/bin/python
print "hello world"
print 4+2
```

ctrl+x and then y to save it

enter this terminal command:
```

python test.py
```

there ya go, you created and ran your first program without leaving the terminal. and, it'll run on pretty much any Linux system you throw it at.

note that python is an interpreted/scripted language... for compiled languages, you will have to use 'make' and other gnu stuff to compile first.

---

### Post by CoffeeRain on 2011-04-27
> **directhex said:**
> The compilers for all of these are not installed by default. Some support for apps written with them may be installed. In the case of scripting languages like Perl, those are the same thing - but for compiled languages, you need to install the compiler package.
Thanks for explaining that! :) Here are some that I can use. I think they are installed by default.
Ruby, Perl, Bash, Python, and I'm sure there are more that I have not used. Hope this helped!

---

