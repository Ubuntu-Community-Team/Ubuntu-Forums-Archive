---
title: "comparing char to int"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by BoilerEE on 2009-11-12
how can I get the ascii value of and int?

I want to compare an int to and int stored as a char, which means I need to compare the ascii values how could I go about doing this I have tried many different ways and have just hit a wall.

THANKS!!!

and btw I am still a programing newb...

---

### Post by travmanx on 2009-11-12
What language are you using? Java/C++/ect

In C++

```
short ASCIIConvert( char value )
    {
      return static_cast&ltshort>(value) - 48;
    }
```

---

### Post by BoilerEE on 2009-11-12
> **travmanx said:**
> What language are you using? Java/C++/ect

In C++

```
short ASCIIConvert( char value )
    {
      return static_cast&ltshort>(value) - 48;
    }
```

I am using C++, and I don't think I can use that function. Is that provided in any of the standard libraries?

basically what I am trying to do is the code below
```

#include<stdio.h>
#include<stdlib.h>
#include<string.h>

int main()
{
  char th,hund,ten,one,th_t,hund_t,ten_t,one_t;
  int year;
  char *yeer;

  yeer = malloc(sizeof(char)*4);
  th_t = '1';
  hund_t = '9';
  ten_t = '9';
  one_t = '0';
  year = 1990;
 
  th=(year/1000);
  hund=((year%1000)/100);
  ten=((year%100)/10);
  one=(year%10);
  if(th==th_t){
  printf("%d %d %d %d\n", th,hund,ten,one);
  printf("%d %d %d %d\n",th_t,hund_t,ten_t,one_t);
  }
  return(0);
}

```

---

### Post by twisted_steel on 2009-11-12
For your future programming questions, there is also a [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") sub-forum on here.

---

### Post by BoilerEE on 2009-11-12
Ok I will move this over there thank you!

---

### Post by travmanx on 2009-11-12
> **BoilerEE said:**
> I am using C++, and I don't think I can use that function. Is that provided in any of the standard libraries?

basically what I am trying to do is the code below
```

#include<stdio.h>
#include<stdlib.h>
#include<string.h>

int main()
{
  char th,hund,ten,one,th_t,hund_t,ten_t,one_t;
  int year;
  char *yeer;

  yeer = malloc(sizeof(char)*4);
  th_t = '1';
  hund_t = '9';
  ten_t = '9';
  one_t = '0';
  year = 1990;
 
  th=(year/1000);
  hund=((year%1000)/100);
  ten=((year%100)/10);
  one=(year%10);
  if(th==th_t){
  printf("%d %d %d %d\n", th,hund,ten,one);
  printf("%d %d %d %d\n",th_t,hund_t,ten_t,one_t);
  }
  return(0);
}

```

You are essentially creating a new function. I don't know of any functions already built in that goes from int to ascii.

USe this as the code

```
#include<stdio.h>
#include<stdlib.h>
#include<string.h>

int main()
{
  char th,hund,ten,one,th_t,hund_t,ten_t,one_t;
  int year;
  char *yeer;

  yeer = malloc(sizeof(char)*4);
  th_t = '1';
  hund_t = '9';
  ten_t = '9';
  one_t = '0';
  year = 1990;
 
  th=(year/1000);
  hund=((year%1000)/100);
  ten=((year%100)/10);
  one=(year%10);
  if(th==th_t){
  printf("%d %d %d %d\n", th,hund,ten,one);
  printf("%d %d %d %d\n",th_t,hund_t,ten_t,one_t);
  }
  ASCIIConvert("a"); //Whatever you'd like here
  return(0);
}

short ASCIIConvert( char value )
    {
      return static_cast&ltshort>(value) - 48;
    }

```

---

### Post by BoilerEE on 2009-11-12
and sorry to everyone if I have two of the same posts I can't figure out how to mark as closed or solved... 

MY BAD


CHANGE-> I got it... lol god I hate being a newb... >_<

---

