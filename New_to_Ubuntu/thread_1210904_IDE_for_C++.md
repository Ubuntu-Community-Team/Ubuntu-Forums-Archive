---
title: "IDE for C++"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by karth83 on 2009-07-12
Which is the best IDE for C++ in Ubuntu?
I have been using TurboC in DOS and Visual Studio in Windows.
I mainly work on Embedded Systems Project. So i dont depend on the OS library. I just want to compile, step by step debug of my application layer C++ code.

---

### Post by JohnnySage50307 on 2009-07-12
Ubuntu has the Codelite IDE for C/C++. I've never actually used it because I often code using the Vim text editor and compile using lint. Some of my friends and people I've taught claim it's a fairly good enviroment.
 
On Windows machines, I grew up using Visual Studios. Having as many years of experience as I do with it, I can find my way around fairly quickly and tailor it to how I need it. People who are new to the VS enviroment, I caution because it's pretty easy to get lost, so find a good tutorial and play with it.
 
One thing you can do is when you compile on the terminal, use the -ggdb flag with gcc or g++; after compiling, if you use "$ gdb *prog*", you can use the gnu debugger and do some pretty nifty things with debugging your code.  There are tutorials for using gdb, so go find them!

---

### Post by Quake on 2009-07-12
One of my favorite is Geany [http://www.geany.org/](http://www.geany.org/).

---

### Post by karth83 on 2009-07-13
Thank You all for your replies :-)

---

### Post by DGortze380 on 2009-07-13
code::blocks is another option.

---

### Post by karth83 on 2009-07-26
> **DGortze380 said:**
> code::blocks is another option.

Yes!! Code Blocks is awesome with too many features. I really liked it a lot. It is far better than many Windows IDE which we pay huge amount. 

Now I am really feeling bad for paying a huge money for a Windows IDE for AVR projects. In Ubuntu it is free and far better

---

### Post by credobyte on 2009-07-26
+1 for Geany ;)

---

### Post by Jimleko211 on 2009-07-26
Both Geany and Code::Blocks are wonderful.

---

### Post by colau on 2009-08-17
> **Jimleko211 said:**
> Both Geany and Code::Blocks are wonderful.
Hello,
Do you have code complete option in Code::Blocks?

---

### Post by colau on 2009-08-17
> **credobyte said:**
> +1 for Geany ;)
Is code complete option available in Geany?

---

### Post by credobyte on 2009-08-17
> **colau said:**
> Is code complete option available in Geany?

As far as I know, no ( attached completion section in preferences ).

---

### Post by colau on 2009-08-17
> **credobyte said:**
> As far as I know, no ( attached completion section in preferences ).
Nothing happens after typing the dot character(.).
```

#include<stdio.h>
#include<iostream>
using namespace std;


struct a{
	int i;
	int j;
};
int main(){
	a obj;
	[COLOR="Red"]**obj.**[/COLOR]
	return 0;
}

```

---

### Post by trilobite on 2009-08-17
> **karth83 said:**
> Which is the best IDE for C++ in Ubuntu?
I have been using TurboC in DOS and Visual Studio in Windows.
I mainly work on Embedded Systems Project. So i dont depend on the OS library. I just want to compile, step by step debug of my application layer C++ code.

Hi - 
 As a number of other have here, I would strongly recommend Geany. It is *excellent*. 
It has a very clean, uncluttered design, and is easy to use. I've seen Code::Blocks but it looks a bit more cluttered than Geany is. 

 Your timing is excellent too, because Geany 0.18 has just been released. Don't be fooled by the version number, btw - Geany is rock-solid. 
Oh, and btw - in the features list for 0.18, I see "Add 'Autocomplete all words in document' pref." 
 - Hope this helps - 
- trilobite

---

