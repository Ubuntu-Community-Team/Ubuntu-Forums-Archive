---
title: "[SOLVED] gcc: no input files"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by ms2756 on 2009-01-04
Hi all,

I have spent a decent amount of time trying to get my gcc to work, but it won't. Here's what I tried:

sudo apt-get install gcc
//told me I had the latest version

gcc -o HelloWorld.c
gcc: no input files

gcc -Wall -ansi HelloWorld.c
//a bunch of stuff, like 
HelloWorld.c:7: error: 'cout' undeclared (first use in this function)

I also used Tab to complete program name, so there are no errors of that sort. Also gcc complained at some point about not recognizing <stdio.h>

Here is my program (copied directly from a book):

include <iostream>

using namespace std;

int main()
{
  cout << "Hello World!" << endl;
  return 0;
}


Thank you very much for any suggestions.
Side note: I have Ubuntu 8.10, installed it yesterday, so should be up to date.

---

### Post by igknighted on 2009-01-04
gcc -o file.c will try to output a file called file.c, and no input file was given.  You would probably want 'gcc file.c -o file.bin', which would input the file file.c, and output the file file.bin

EDIT: replace those first two lines in your file with '#include <stdio.h>'

What book are you using?  That's some pretty odd looking C code...

EDIT #2: You might need some additional libraries to compile... try installing the package build-essential too

---

### Post by anewguy on 2009-01-04
I'm trying to remember, but isn't cout a C++ function?  If so, have you tried using g++ in place of gcc?

Dave

---

### Post by MighMoS on 2009-01-04
> **ms2756 said:**
> Hi all,

I have spent a decent amount of time trying to get my gcc to work, but it won't. Here's what I tried:

sudo apt-get install gcc
//told me I had the latest version

gcc -o HelloWorld.c
gcc: no input files

gcc -Wall -ansi HelloWorld.c
//a bunch of stuff, like 
HelloWorld.c:7: error: 'cout' undeclared (first use in this function)

I also used Tab to complete program name, so there are no errors of that sort. Also gcc complained at some point about not recognizing <stdio.h>

Here is my program (copied directly from a book):

include <iostream>

using namespace std;

int main()
{
  cout << "Hello World!" << endl;
  return 0;
}


You need g++. Also, you have a .c extension, which the compiler will assume to be C (not C++). Using .cc or .cpp is recommended, instead. So in the end your command to compile and run your program will look something like ```
g++ HelloWorld.cc -o HelloWorld
./HelloWorld
```

---

### Post by ken22 on 2009-01-04
There is nothing wrong with your original code, it's just not C it's C++.

g++ is the linux c++ compiler.

---

### Post by ms2756 on 2009-01-04
Thanks to all. I changed my code to the following and I installed/compiled with g++.


#include <stdio.h>

int main()
{
  cout << "Hello World!" << endl;
  return 0;
}

I got:
HelloWorld.cpp: In function 'int main()':
HelloWorld.cpp:5: error: 'cout' was not declared in this scope
HelloWorld.cpp:5: error: 'endl' was not declared in this scope

I get the same errors when I follow MighMoS' suggestions: changing to .cc or .cpp makes no difference, nor does -o.
But thanks anyway.

Any suggestions?

---

### Post by ken22 on 2009-01-04
Yes,

If you want this to compile as C++, try: 

```

#include <iostream>

using namespace std;

int main()
{
cout << "Hello World!" << endl;
return 0;
}
```

stdio.h is a C header not C++

cout is defined in iostream and you must declare that you're using namespace std;

I use the extension .cpp as it is standard practice, at least where I work.

---

### Post by ken22 on 2009-01-04
A C version would be

```

#include <stdio.h>

int main()
{
    printf("Hello World");
    return 0;
}

```

---

### Post by igknighted on 2009-01-04
> **ms2756 said:**
> Thanks to all. I changed my code to the following and I installed/compiled with g++.


#include <stdio.h>

int main()
{
  cout << "Hello World!" << endl;
  return 0;
}

I got:
HelloWorld.cpp: In function 'int main()':
HelloWorld.cpp:5: error: 'cout' was not declared in this scope
HelloWorld.cpp:5: error: 'endl' was not declared in this scope

I get the same errors when I follow MighMoS' suggestions: changing to .cc or .cpp makes no difference, nor does -o.
But thanks anyway.

Any suggestions?

I made those suggestions assuming you were trying to compile C code, you should leave it if using C++.

---

### Post by ms2756 on 2009-01-04
Thanks a lot everybody. It did compile and gave out a.out.
Before I just naturally assumed that C++ encompasses C, just like Java contains all of its previous versions (for the most part). I guess C++ !> C.

Now what do I do with a.out? Apparently, I don't have an "exec" function.
Is there something else? Tried apropos exec - not useful.
Suggestions?

---

### Post by igknighted on 2009-01-04
> **ms2756 said:**
> Thanks a lot everybody. It did compile and gave out a.out.
Before I just naturally assumed that C++ encompasses C, just like Java contains all of its previous versions (for the most part). I guess C++ !> C.

Now what do I do with a.out? Apparently, I don't have an "exec" function.
Is there something else? Tried apropos exec - not useful.
Suggestions?

./a.out to run the file.

---

### Post by ken22 on 2009-01-04
> **ms2756 said:**
> 
Now what do I do with a.out? Apparently, I don't have an "exec" function.
Is there something else? Tried apropos exec - not useful.
Suggestions?

To run a.out

```
./a.out
```

from the directory it is in.

---

### Post by ms2756 on 2009-01-04
Yup, thanks.
How do I close this question? (I heard some people complain about resolved questions still being open).

---

### Post by igknighted on 2009-01-04
At the top of the page, click "thread tools" -> Marked as solved

---

