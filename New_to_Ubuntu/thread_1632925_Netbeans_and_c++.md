---
title: "Netbeans and c++"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by Maelzel on 2010-11-28
Hello Ubuntu Community,


I recently purchased a new computer and decided to try Ubuntu, it seems like a capable OS but I'm very inexperienced with computers (I haven't owned one in awhile). I bought the computer so I could try my hand at coding, I have a little experience with Java and C++. I thought I would use vim as an IDE for c++ but decided instead to use netbeans. I'm trying to make the hello world program but am having trouble compiling and running programs using netbeans. First netbeans said it was unable to resolve the identifiers "std" and "using" but I went into tools>options>c and c++ and was able to resolve this using online resources. The current problem I face is that netbeans successfully compiles and runs the program but when a terminal window opens it says "press [enter] to close the terminal" and doesn't display Hello World!. This is the code I used:

//hello world
#include <iostream>
using namespace std;

int main()
{
    cout << "Hello World!";
    return 0;
}

Any ideas why it won't display?

Thank you for your help, hopefully once I've mastered the learning curve I will be able to make a more active contribution to the community :D

---

### Post by yankysunny on 2010-11-28
The only thing that came into my mind is that netbeans is unable to find some identifiers. I order to solve this look at this post [http://soledadpenades.com/2009/11/25/netbeans-unable-to-resolve-identifier-std-error/](http://soledadpenades.com/2009/11/25/netbeans-unable-to-resolve-identifier-std-error/)

---

### Post by Maelzel on 2010-11-28
Yup, that's one of the places I went in order to resolve the issue. The problem I have now is the message "Hello World!" not displaying in terminal. I'm no longer getting any errors, it's just not displaying the cout.

---

### Post by yankysunny on 2010-11-28
If it compiles and run without any errors, then it must had displayed "hello world" 
try to use getch() function at the end or may be insert some loops to see if display anything or not

---

