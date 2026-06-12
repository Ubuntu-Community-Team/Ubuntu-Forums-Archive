---
title: "Beginners for programming"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by CaptainMark on 2010-07-19
Im interested in starting to learn how to do computer programming. Can anyone recommend any books which are tried and tested for beginners. Also which language do you think is the easiest for a beginner to learn on?

---

### Post by Kay The Bantu on 2010-07-19
I'd recommend python, because there's a boat load of resources for the absolute beginner, plus its fairly easy and hella powerful. For starters go here [http://www.swaroopch.com/notes/Python]("http://www.swaroopch.com/notes/Python") for a guide, thats after installing the IDE ofcourse (hint:search synaptic)

---

### Post by Legendary_Bibo on 2010-07-19
Python for shizzle

The syntax is easier to deal with, it's very flexible. It's great for making little applications that don't require memory optimization and whatnot.

---

### Post by Legendary_Bibo on 2010-07-19
> **Kay The Bantu said:**
> I'd recommend python, because there's a boat load of resources for the absolute beginner, plus its fairly easy and hella powerful. For starters go here [http://www.swaroopch.com/notes/Python](http://www.swaroopch.com/notes/Python) for a guide, thats after installing the IDE ofcourse (hint:search synaptic)

Yeah, and I'd recommend Geany as a great IDE.

---

### Post by Kay The Bantu on 2010-07-19
> **Legendary_Bibo said:**
> Yeah, and I'd recommend Geany as a great IDE.

Couldn't agree more on Geany

---

### Post by CaptainMark on 2010-07-19
googled geany and it looks good, ill check that out. thanks

---

### Post by Legendary_Bibo on 2010-07-19
> **CaptainMark said:**
> googled geany and it looks good, ill check that out. thanks

yeah and I'm going to save you a bit of time and tell you that for a python program, you have to write this on your first line

```

#!/usr/bin/env python

```

Also it's best to save as *someapplicationname.py* this will let geany know that you're writing in python so it can change the indentations for you automatically. Here's an example of a python program for you I wrote. It does the quadratic equation for you.

```

#!/usr/bin/env python

import math

a = input('a? ')

b = input('b? ')

c = input('c? ')

root = (b**2)-(4*a*c)
if root < 0:
    positive = "imaginary root" 
    negative = "imaginary root"
    print "positive = ", positive
    print "negative = ", negative
elif root >= 0:
    positive = (-b+math.sqrt(root))/(2*a)
    negative = (-b-math.sqrt(root))/(2*a)
    print "positive = ", positive
    print "negative = ", negative

raw_input()

```

and another one that displays the taylor polynomial of e^x, just not horizontally like it should.

```

#!/usr/bin/env python

import math

print "This program will print off the taylor polynomial of e^x of"
print "whatever degree you would like"

n = input('degree? ')
exponent = 0
passthrough = 0

while exponent != n:
    if passthrough >= 1:
        exponent = exponent + 1
    if exponent == n:
        print "x^", n , " +"
        print "_____"
        print math.factorial(n)
        break
    print "x^", exponent, " +"
    print "_____"
    print math.factorial(exponent)
    print ""
    print ""
    passthrough = passthrough + 1
    

raw_input()

```

I also recommend putting that

```
raw_input()
```

command at the end of each program so it doesn't close the terminal right away.


While we're on the topic of Geany does anyone know how when you're typing in a loop or an if statement, how do break out of it (not a break statement), but actually get out of the indentation to write something below it?

---

### Post by petrus250 on 2010-07-19
If it works under wine, I would highly recommend either greenfoot or bluej as java starters. :-D

---

### Post by da burger on 2010-07-19
Can I put in a word for ruby? It's a great language with dead simple syntax rules. It's also pure OOP which means everything in the entire language follows a very small set of rules.

[http://pine.fm/LearnToProgram/](http://pine.fm/LearnToProgram/) << that is also a good tutorial to get you started.

Couldn't agree more with geany.

---

### Post by anewguy on 2010-07-19
I suppose this also depends on what you want your program to do.  Do you want it to have a GUI'd interface?  If so, I *think* you'll also need to learn GTK+ (I haven't used Python yet, but I was under the impression it doesn't have the tools for developing a "windowed" application - someone correct me if I'm wrong, please!).

Dave

---

### Post by da burger on 2010-07-19
Python has tk bindings if I remember correctly. However if your just starting out GUIs shouldn't be your priority. Learn the basics and get into good coding habits, then look into GUIs and other more complex features.

---

### Post by emoguitarist06 on 2010-07-19
**Great Topic!**

I think I may also take the suggestions and learn python

I did VisualBasic in 2002 when I was a freshman in Highschool and I was #1 in my class LOL so hopefully I should be pick up python quickly.

---

### Post by Penguin Guy on 2010-07-19
I'd advise [Bash]("http://linuxcommand.org/") then [Python]("http://docs.python.org/tutorial/").

---

### Post by Linux000 on 2010-07-19
Python and Geany, simple to use, don't even have to write the header '!# /bin/env python' or deal with separate editors and compilers, all done right there.

---

### Post by ankit singh on 2010-07-19
I have read many sites and every sites i saw, said learning python is the best way to start programming for beginners.Start with a easy book and then as you build confidence start taking challenging problems(which are found in advance books).However you can start with any language you like like c(not c++),java,etc its not a compulsion.Once you feel confident learn other languages.A good hacker knows atleast dozen language.

---

### Post by CaptainMark on 2010-07-22
ive bought myself a book on python for beginners, i notice python has a ppa, should i add it to keep up to date or will i not notice until i move to advanced stuff??

---

### Post by Vaphell on 2010-07-22
don't bother

[http://www.youtube.com/view_play_list?p=EA1FEF17E1E5C0DA](http://www.youtube.com/view_play_list?p=EA1FEF17E1E5C0DA)
check out this tutorial, really good

---

### Post by Lektorvis on 2012-01-14
> **petrus250 said:**
> If it works under wine, I would highly recommend either greenfoot or bluej as java starters. :-D

Greenfoot installs with ease on Ubuntu, get it her: [http://www.greenfoot.org/download/files/greenfoot-212.deb]("http://www.greenfoot.org/download/files/greenfoot-212.deb") 

Great learning program.

---

