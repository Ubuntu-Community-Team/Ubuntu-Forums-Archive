---
title: "Geany runtime problem........"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by vishwasmeshram on 2010-06-17
Last night i install the GEANY for the c programming.............
i successfully run the Helloworld program in it...
then i try out new program which is compiled successfully but when i try to run it gives me error...
plz help.........

code of the programe is as follow:-


#include<stdio.h>
main()
{
    int i=10;
    while(i<0)
    {
      printf("\n Rocker");
      i--;
    }
}



And the error is :-
program exited with code:132


plz help

---

### Post by SwatKat on 2010-06-17
> **vishwasmeshram said:**
> Last night i install the GEANY for the c programming.............
i successfully run the Helloworld program in it...
then i try out new program which is compiled successfully but when i try to run it gives me error...
plz help.........

code of the programe is as follow:-


#include<stdio.h>
main()
{
    int i=10;
    **while(i<0)**
    {
      printf("\n Rocker");
      i--;
    }
}



And the error is :-
program exited with code:132


plz help

Not a geany problem. Wrong code. You'll have to change condition to **while (i>0)** since you have initialized i to 10 and are decrementing it.

---

### Post by vishwasmeshram on 2010-06-17
i have changed my code .........it compile successfully.......but doesnt show output in output window

#include<stdio.h>
main()
{
    int i=10;
    while(i>0)
    {
        printf("\n Rocker");
        i++;
    }
}

---

### Post by vishwasmeshram on 2010-06-17
> **SwatKat said:**
> Not a geany problem. Wrong code. You'll have to change condition to **while (i>0)** since you have initialized i to 10 and are decrementing it.
i have changed my code .........it compile successfully.......but doesnt show output in output window

#include<stdio.h>
main()
{
    int i=10;
    while(i>0)
    {
        printf("\n Rocker");
        i++;
    }
}

---

### Post by RTrev on 2010-06-17
> **vishwasmeshram said:**
> i have changed my code .........it compile successfully.......but doesnt show output in output window

#include<stdio.h>
main()
{
    int i=10;
    while(i>0)
    {
        printf("\n Rocker");
        i++;
    }
}

Don't know, but maybe Geany won't flush the output buffer until output stops?  And output will never stop with your code.  Your variable i will start at 10, and then continue incrementing to 11, 12, 13, 14, ad infinitum.  So i will *always* be greater than zero.

Try seeing if decrementing i (i--) will cause it to output everything once it's done running.

---

