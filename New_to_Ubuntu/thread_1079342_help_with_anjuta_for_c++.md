---
title: "help with anjuta for c++"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by bamdad on 2009-02-24
Hi guys, i have recently shifted to Linux and i need to start coding some c++. i decided to use anjuta since it seems like a good and friendly IDE. i used to code in Dev-c++ but coding in linux seems a bit more complicated. anyways, i was wondering if you guys could help me out in understanding Anjuta. by the way i have read some tutorials too.

 my main problems is when i want to include some .h file that i have written myself. when i type in #include <"my header files name".h> how am i supposed to tell the compiler to find the header file?(except for changing the makefiles manually). i have decided right clicking on the main.cpp script in the project file list and change the properties of this file. there i can open up a window which allows me to add some compiler flag options and stuff.. i typed the address to my header file in this window in a box in front of the "libraries" but it didnt work and im feelin kinda confused. i have also come to understand that i cannot include my header files in the usr/include directory of ubuntu (i guess this is used for installed libraries right?) so could you guys help me out with this problem? im using anjuta 2.4.1

thnx

---

### Post by rgb96 on 2009-02-24
Sorry I can't be too much help, because I just use gedit and g++, but whenever I have needed to include user made .h files, no matter what OS or compiler, I've never had problems when I make sure there is a copy of the .h in the same directory of the file I'm trying to compile.

---

### Post by bamdad on 2009-02-24
thank you, this solves the problem for now. but how can i actually create some library that could be accessed by multiple programs? basically i want to write some scripts and classes to do computational calculations and use them in multiple programs. so can you guys help me understand how i should create libraries? its obvious,im not that much of an expert in coding/

---

