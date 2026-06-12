---
title: "Looking for advice on learning c/c++"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by celticbhoy on 2009-03-07
After a couple of years using Ubuntu, I would now like to learn how to code in c/c++. To give a bit of background, it has been a number of years since I coded, and then it was visual basic, and pascal.

What I want to know is the best IDE to use, and any online resources to use, tutorial sites would be a bonus. I have googled and been completely snowed under by the amount of options, so I would like advice on the best way to go.


Thanx in advance for any help.

---

### Post by DGortze380 on 2009-03-07
> **celticbhoy said:**
> After a couple of years using Ubuntu, I would now like to learn how to code in c/c++. To give a bit of background, it has been a number of years since I coded, and then it was visual basic, and pascal.

What I want to know is the best IDE to use, and any online resources to use, tutorial sites would be a bonus. I have googled and been completely snowed under by the amount of options, so I would like advice on the best way to go.


Thanx in advance for any help.

Basic tutorials, you can't beat [http://www.cprogramming.com/](http://www.cprogramming.com/)


When starting out:

I would suggest a basic text editor, I prefer vim, and command line g++.

geany if nice for simple code as well.

For a full IDE, I've heard goo things about eclipse, but I use Xcode and OS X my self so some one else will have to chime in about that.

---

### Post by celticbhoy on 2009-03-07
I have installed eclipse, but it looks over complicated for beginners use to me, might be wrong will take advice on that though. Will have a look at your tutorial advice, I had a look at one and although it was clear and easy, the actual syntax was wrong for the GNU G++ installed in Ibex.

---

### Post by DGortze380 on 2009-03-07
> **celticbhoy said:**
> I have installed eclipse, but it looks over complicated for beginners use to me, might be wrong will take advice on that though. Will have a look at your tutorial advice, I had a look at one and although it was clear and easy, the actual syntax was wrong for the GNU G++ installed in Ibex.

shouldn't be. check for typos, or post the code here and we can help you debug it.

---

### Post by celticbhoy on 2009-03-07
This is the first little prog :-

\* 0001_hello.cpp *\
#include <iostream>
using namespace std;
int main()
{
	cout << end1 << "Hello World";;
	return 0;
}

As I say it wont compile, and even the line explaining how to compile gives invalid options. with an unknown option in -q

---

### Post by DGortze380 on 2009-03-07
> **celticbhoy said:**
> This is the first little prog :-

\* 0001_hello.cpp *\
#include <iostream>
using namespace std;
int main()
{
	cout << end1 << "Hello World";;
	return 0;
}


Don't need any options for this simple program.

Line 5: endl  (lowercase L)  not  end1
Line 5: one ;  not two

fix that and run

g++ hello.cpp -o hello
(replace hello w/ your file name)

./hello

---

### Post by celticbhoy on 2009-03-07
OK first appologies for typo's :redface:

But still getting this on compile :-

hello.cpp:1: error: stray ‘\’ in program
hello.cpp:1:4: error: invalid suffix "_hello.cpp" on integer constant
hello.cpp:1: error: stray ‘#’ in program
hello.cpp:1: error: expected unqualified-id before numeric constant
hello.cpp:1: error: expected constructor, destructor, or type conversion before numeric constant
hello.cpp: In function ‘int main()’:
hello.cpp:6: error: ‘cout’ was not declared in this scope
hello.cpp:6: error: ‘endl’ was not declared in this scope


Any Ideas ?

---

### Post by DGortze380 on 2009-03-07
> **celticbhoy said:**
> OK first appologies for typo's :redface:

But still getting this on compile :-

hello.cpp:1: error: stray &#8216;\&#8217; in program
hello.cpp:1:4: error: invalid suffix "_hello.cpp" on integer constant
hello.cpp:1: error: stray &#8216;#&#8217; in program
hello.cpp:1: error: expected unqualified-id before numeric constant
hello.cpp:1: error: expected constructor, destructor, or type conversion before numeric constant
hello.cpp: In function &#8216;int main()&#8217;:
hello.cpp:6: error: &#8216;cout&#8217; was not declared in this scope
hello.cpp:6: error: &#8216;endl&#8217; was not declared in this scope


Any Ideas ?

Sorry, my version of g++ accepted your comments, but they are incorrect.

try using a single line comment on the first line.

// This is a C++ single line Comment

/* This is a correct C++ Style
Block Comment */

---

### Post by celticbhoy on 2009-03-07
OK that done the trick, but I would still rather take my first steps with a tutorial that wont have any version issues. Anyone point me in the right direction.

---

### Post by DGortze380 on 2009-03-07
> **celticbhoy said:**
> OK that done the trick, but I would still rather take my first steps with a tutorial that wont have any version issues. Anyone point me in the right direction.

again, cprogamming.com

there are no syntax issue with the compiler, ANSI C++ is ANSI C++ regardless of the compiler.

[http://www.cprogramming.com/tutorial/lesson1.html](http://www.cprogramming.com/tutorial/lesson1.html)

---

### Post by celticbhoy on 2009-03-07
Cheers DGortez will give it a go - thanx for you time.

---

### Post by celticbhoy on 2009-03-07
Just one last question (hopefully), in the tutorial it states that on some c++ version the IDE will compile for you, is there an IDE for Linux GNU C++ that does that??

---

### Post by DGortze380 on 2009-03-07
> **celticbhoy said:**
> Just one last question (hopefully), in the tutorial it states that on some c++ version the IDE will compile for you, is there an IDE for Linux GNU C++ that does that??

Any mainstream Linux IDE is going to use g++. Most IDE's will give you a 'compile button', but ultimately it's just passing commands to the command line.

For any of those tutorials, compiling is no more difficult than the hello world you just wrote.

---

