---
title: "I'm learning c++ and ran into a small snag"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by robgraves on 2011-02-28
I bought a "C++ for Dummies book" just started reading it and doing example code from the book in Code:Blocks 10.05, I'm running ubuntu 10.10 btw.  anyway my exact code:
```
//
//   Conversion - Program to convert temperature from
//   Clesius degrees into Fahrenheit:
//   Fahrenheit = Celsius  *  (212 - 32)/100 + 32
//
#include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;

int main(int nNumberofArgs, char* pszArgs[])
{
    // enter the temperature in celsius
    int celsius;
    cout << "Enter the temperature in Celsius:";
    cin >> celsius;

    // calculate conversion factor to convert celsius
    // into fahrenheit
    int factor;
    factor = 212 - 32;

    // use conversion factor to convert celsius
    // into fahrenheit values
    int fahrenheit;
    fahrenheit = factor * celsius/100 +32;

    // output the results (followed by a newline)
    cout << "Fahrenheit value is:";
    cout << fahrenheit << endl;

    // wait until user is ready before terminating program
    // to allow the user to see the program results
    system("PAUSE");
    return 0;
}

```it compiles ok, and runs the program properly by asking me for temperature in celsius, and reads me back the conversion in fahrenheit, however at the very end i get as output:
```
sh: PAUSE: not found
```

Anyone have any insight as to why this happens would be appreciated as the book states it should simply state "Press any key to continue..."  which it does do but after the sh: PAUSE: not found message.

---

### Post by anglican on 2011-02-28
> **robgraves said:**
> I bought a "C++ for Dummies book" just started reading it and doing example code from the book in Code:Blocks 10.05, I'm running ubuntu 10.10 btw.  anyway my exact code:
```

   ...snip...
   system("PAUSE");

```it compiles ok, and runs the program properly by asking me for temperature in celsius, and reads me back the conversion in fahrenheit, however at the very end i get as output:
```
sh: PAUSE: not found
```Anyone have any insight as to why this happens would be appreciated as the book states it should simply state "Press any key to continue..."  which it does do but after the sh: PAUSE: not found message.Take a look at:

[http://www.gidnetwork.com/b-61.html](http://www.gidnetwork.com/b-61.html)

Basically > "It's not portable. This works only on systems that have the PAUSE command at the system level, like DOS or Windows. But not Linux and most others..."
H

---

### Post by seawolf167 on 2011-02-28
> **robgraves said:**
> system("PAUSE");

Is a terrible Windows specific command, for linux systems you'll want to use

```
cin.get();
```

---

### Post by robgraves on 2011-02-28
excellent, that worked thank you

---

### Post by cgroza on 2011-02-28
Terrible thing, I had the same problem with my python tutorials... Had to use raw_input.

---

### Post by robgraves on 2011-02-28
> **cgroza said:**
> Terrible thing, I had the same problem with my python tutorials... Had to use raw_input.

i actually wanna learn python too, that's probably next on my list.

---

### Post by sarsbretta on 2011-04-04
Thank you. It helped me out too.

> **robgraves said:**
> excellent, that worked thank you

---

