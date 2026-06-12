---
title: "c++ cin does not work"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by gwbcomm on 2010-03-28
It does not matter which IDE I use for C++, I get an error when I put "cin >> i;" in a source. All of the IDE's: Codelite, Netbeans, and Anjuta  are using GNU g++. Codelite gives the errors 
47: error: ‘cout’ was not declared in this scope
49: error: ‘cin’ was not declared in this scope.

When I change to Cobra in Codelite, the errors go away. What am I doing wrong?

---

### Post by marshmallow1304 on 2010-03-28
Do you have
```
#include <iostream>
using namespace std;
```
at the top?

---

### Post by gwbcomm on 2010-03-28
using namespace std; is in the program.

---

### Post by derekeverett on 2010-03-28
> **gwbcomm said:**
> using namespace std; is in the program.

But is it before your functions? You seem to have a scope issue.

---

### Post by sandyd on 2010-03-28
> **gwbcomm said:**
> It does not matter which IDE I use for C++, I get an error when I put "cin >> i;" in a source. All of the IDE's: Codelite, Netbeans, and Anjuta  are using GNU g++. Codelite gives the errors 
47: error: ‘cout’ was not declared in this scope
49: error: ‘cin’ was not declared in this scope.

When I change to Cobra in Codelite, the errors go away. What am I doing wrong?
for some weird reason, in my computer, the C++ libraries are not added properly... but
```

#include <stdio.h>
#include <stdlib.h>
#include </usr/lib/c++/4.4.1/string>
#include </usr/lib/c++/4.4.1/iostream>

```
Ive included the absolute paths to the libraries just in case.

---

### Post by gwbcomm on 2010-03-30
my code is below

#include <stdio.h>


using namespace std;


int main ()
{
  char c;
  int r;
  puts ("Enter text. Include a dot ('.') in a sentence to exit:");
  do {
    c=getchar();
    cin >> r;
    putchar (c);
  } while (c != '.');
  return 0;
}

the error is
:43: error: &#8216;cin&#8217; was not declared in this scope

---

### Post by schauerlich on 2010-03-30
You're mixing C and C++. stdio.h is C's IO library, iostream is C++'s.

```
#include <iostream>
#include <string>

using namespace std;

int main () {
  string s;
  
  cout << "Say something: ";
  cin >> s;
  cout << "You said: " << s << endl;

  return 0;
}
```

---

### Post by gwbcomm on 2010-03-30
you are my hero. I have spent days on the net trying to resolve. I have seen hundreds of posts elsewhere with this problem. I am happy for tonight. maybe now I can continue with my app. Got a way to validate number input (nnnn.nnn)?

You have a great day

Thanks

---

