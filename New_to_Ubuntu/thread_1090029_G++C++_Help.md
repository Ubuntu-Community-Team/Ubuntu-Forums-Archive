---
title: "G++/C++ Help"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by The13thbrother on 2009-03-07
Hey, I'm very new to Ubuntu and C++. Having only installed Ubuntu yesterday and tried out c++ about 10 minutes ago. I installed g++ to make my programs work and when i try to run it using terminal i type in this: 

"g++ hello.cpp -o hello" (no quotes)

i get this:

"g++: hello.cpp: No such file or directory
g++: no input files"


here is my program:

//include this for cout
#include <iostream.h>

int main() {

   //print out the text string, "Hello, World!"
   cout << "Hello, World!" << endl;

   return 0;

}

and i am saving to desktop

am i typing something wrong, am i saving wrong? do i need to save to a g++ folder and if i do, how?

thanks for your help!

---

### Post by DGortze380 on 2009-03-07
open a terminal and type

cd Desktop

then try g++ again.

You need to run g++ in the directory in which your source file is located.

OR

Use absolute paths (replace <> with your username)

g++ /home/<username>/Desktop/hello.cpp -o /home/<username>/Destkop/hello



PS-

You're going have compile errors.
You should choose one fo the following options for your source code

```

//include this for cout
#include <iostream.h>

**using namespace std;**

int main() {

//print out the text string, "Hello, World!"
cout << "Hello, World!" << endl;

return 0;

}

```

OR

```

//include this for cout
#include <iostream.h>

int main() {

//print out the text string, "Hello, World!"
**std::**cout << "Hello, World!" << endl;

return 0;

}

```

Last tip. <iostream.h> is typically used in C, you should use <iostream> for ANSI C++ code.

---

### Post by ekaqu on 2009-03-07
> here is my program:

//include this for cout
#include <iostream.h>

int main() {

   //print out the text string, "Hello, World!"
   cout << "Hello, World!" << endl;

   return 0;

}

your code is the issue.

#include <iostream.h>  //this is c style
#include <iostream> //this is c++ style

using namespace std;  //needed to use anything from std libs



//include this for cout
#include <iostream>
using namespace std;
int main() {

//print out the text string, "Hello, World!"
cout << "Hello, World!" << endl;

return 0;

}

Use this code and it will work.  c++ has some small differences from c that you have to watch out for.

---

