---
title: "ASCII Special Characters"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by nayeret43 on 2009-01-03
In my Netbeans, I have entered the following code:

```


#include <iostream>
using namespace std;
int main()
{
    for(int i=0; i<255; i++)
        cout << char(i) << endl;
    
    return 0;
}


```

It is supposed to print out all the ascii characters.  Why doesn't it do this?  It just prints out a bunch of question marks where the special characters are supposed to be.....

---

### Post by Bachstelze on 2009-01-03
Special characters are, well, special. They are not printable, so this is normal.

---

### Post by nayeret43 on 2009-01-03
Okay, well I will rephrase my question.

I want to print out special ASCII characters, but it doesn't seem to work.

How do I get it to work?

---

### Post by The Cog on 2009-01-03
Firstly, ASCII only specefies character codes up to 127. Beyond that, they're not ASCII. But that's just names.

Secondly, many of the codes in the range 0-255 are not printable. Many systems will print a ? in place of a character they can't print. So getting question marks is to be expected.

Thirdly, what characters are you trying to print? They aren't necessarily represented by values in the range 0-255. Ubuntu uses Unicode which can have 16-bit character codes though not all values are valid. Applications->Accessories->Character Map will give you a GUI where you can look up the character code values you want.

---

