---
title: "c++ in ubuntu"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by Ramprasath on 2010-08-31
:confused::(:icon_frown:i am new to ubuntu and i have a problem using c++ 
wat should i do?

---

### Post by Bölvaður on 2010-08-31
what are you trying to do?:confused:


you will need to have a compiler
[sudo apt-get install g++]("apt:g++")

you might not need this...
[sudo apt-get install build-essential]("apt:build-essential")

then you'll need something like...
[sudo apt-get install geany]("apt:geany")
you can just use any text editor really though.

This is what I got in "Set includes and arguments", which allows me to have different compilation parameters depending on what type of programming Im doing.
this is what I got at the moment
> build:
g++ -Wall -lglut -o "%e" "%f"
compile:
g++ -o "%e" "%f"



this is how you compile normally
> g++ ./file.cpp -o ./file && ./file


this is an example of it
> cd /home/decae/projects/foo
g++ foo.cpp -o foo
./foo

---

### Post by KdotJ on 2010-08-31
Do you mean running programs in C++ or writing and compiling them?

---

### Post by 3Miro on 2010-08-31
> **Ramprasath said:**
> :confused::(:icon_frown:i am new to ubuntu and i have a problem using c++ 
wat should i do?

If you want to learn C++, check out on-line tutorials, buy a book or sign up for a class. C++ is C++ regardless whether or not you use Ubuntu or Windows.

IF you want to install C++ in Ubuntu, follow the instructions on post #2 or simply go to System -> Admin -> Synaptic Package Manager, then search and install g++, build-essentials and geany.

---

### Post by limestone on 2010-08-31
If you're looking for a IDE I recommend geany.

---

