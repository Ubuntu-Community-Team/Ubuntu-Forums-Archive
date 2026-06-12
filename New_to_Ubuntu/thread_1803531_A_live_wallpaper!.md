---
title: "A live wallpaper?!"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by Fawk3s on 2011-07-13
Guys! I'm very excited about this! I just wrote a simple program which generates random numbers and random spaces and keeps moving ( like one of those things you saw in the matrix and numerous other movies, but you always knew what a piece of crap! :) )

Anyway, I actually kept staring at the beautiful effect it created for at least a minute! 

Guys, any idea how do I make this as wallpaper?! Like a live wallpaper with all the numbers running around in the background... I know I'd get fed up after a few hours :P but I think it'd be cool until such time :)

( Just in case you want to know the effect, try running the following piece of code after making your terminal font colour as green with a black background :). But I hope you have a good processor.. or i think it may lag..)

```
/* This program will attempt to create a matrix type simulation */


#include <iostream>
#include <cstdlib>

using namespace std;

int main()
{
        int i,x=0, nbr, spc;
        while(1)
        {
        x = 0;
        {
//      generate the random space value
        spc = rand();
        spc %= 50;
        for(i=0;i<spc;i++)
                cout << " ";
// Now generate the random number
        nbr = rand();
        nbr %= 100;
        cout << nbr;
        x++;
        }
        }
}
```Of course, hit CTRL + C to stop the program :)

---

### Post by CatKiller on 2011-07-13
This kind of thing was a common customisation a while back. If you look for something like "drawing xscreensaver on the root window" you'll probably get some results that will point you in the right direction.

---

### Post by haqking on 2011-07-13
glmatrix screensaver, built in by default i believe

---

### Post by Fawk3s on 2011-07-13
> **CatKiller said:**
> This kind of thing was a common customisation a while back. If you look for something like "drawing xscreensaver on the root window" you'll probably get some results that will point you in the right direction.

hmmm... xscreensaver looks interesting... although it comes with its own set of screensavers which one can use, I believe there is some flexibility to add some of your as well... I'd spend some time on this... Thanks for the info, CatKiller!

---

### Post by Fawk3s on 2011-07-13
> **haqking said:**
> glmatrix screensaver, built in by default i believe

Yeah, built in... you'll never get that satisfaction you know... :)

---

