---
title: "more gcc help"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by lanzcc on 2009-09-15
Greetings,

Can anyone direct me to a moderately complete list of gcc compile-time errors, with at least a bit of information about each entry?

I need to know about ¨stray \302¨ sorts of things. I am unable to successfully compile the following code in gcc, although my el cheapo downloaded c compiler ¨miracle C¨ in Windows OS compiles and executes it just fine:


#include <stdio.h>
#include <string.h>

int ii = 2345;

main(void) 
{

  printf(¨%d¨,ii);

}

here are the errors:
test.c:10: error: stray ‘\302’ in program
test.c:10: error: stray ‘\250’ in program
test.c:10: error: expected expression before ‘%’ token
test.c:10: error: stray ‘\302’ in program
test.c:10: error: stray ‘\250’ in program
test.c:10: warning: format not a string literal and no format arguments


I fear it may have something to do with another weirdness: I am unable to generate either single or double quotes from the keyboard in a normal way. The only way I can get them is to press the key twice. Here&#347; the list that behave this way:

 ¨ ´ ` ^~

HELP?

---

### Post by stumbleUpon on 2009-09-15
The problem is because you dont have proper double quotes in your printf statement. The code compiled and worked perfectly on my machine.

You say that you cant generate double quotes on your machine. Is this a generic problem with your keyboard or is it due to the editor that you used to enter the above code?

Try some other editor (gedit for example from Applications > Accessrories > Text Editor) and see if you can run the program.

---

### Post by cmay on 2009-09-15
I could not compile the example you posted and got the same errors. but this you will be able to copy and compile just fine. It is the quotes that gives the error message. I dont know what up with your keyboard but the error lies in that . 
```
#include <stdio.h>
#include <string.h>

int ii = 2345;

int main(void)
{

      printf("%d",ii);
        
     return 0;
 
}
```

Hope it helped even I cant provide any solution .

---

### Post by muteXe on 2009-09-15
If you try and type a "@" do you get double quotes?

---

