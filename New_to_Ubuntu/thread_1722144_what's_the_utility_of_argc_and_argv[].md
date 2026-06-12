---
title: "what's the utility of argc and argv[]?"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by sirinabb on 2011-04-05
hello all, 
i want to write a program with C on linux and i don't know what's the utility of  (int argc, argv[]) which we find always in the header of main function ???
and can i change thoes variables with others (for example int a, float b) ???
i hope you would help me as soon as possible
thnk youuuu :P

---

### Post by Daniel0108 on 2011-04-05
> **sirinabb said:**
> hello all, 
i want to write a program with C on linux and i don't know what's the utility of  (int argc, argv[]) which we find always in the header of main function ???
and can i change thoes variables with others (for example int a, float b) ???
i hope you would help me as soon as possible
thnk youuuu :P

These are argument storages. argc stores the number of arguments, argv is an array of all arguments.
You start your program, for exmaple:
```
./program --help test
```
argv[0] will be "./program"
argv[1] will be "--help"
and argv[2] will be "test".
argc will be 3 (because there are three items in the array).

I won't change these vars in the main function, but in other functions you can change these vars, of course.

I hope this helped you,
Daniel

---

### Post by TeoBigusGeekus on 2011-04-05
argc: argument count - the number of arguments with which you call your C program. It's a number (obviously); an integer.

argv: argument vector - the actual arguments with which your program is called. It's a pointer to an array of pointers to characters (strings); char *argv[] or char **argv.

For example, let's say that you've created a program that accepts options and switches and you call it like this:
```
./mysuperprogram -erase_internet -kill_RIAA -completely -seriously -but_leave_porn
```
argc=6
argv[0]=mysuperprogram
argv[1]=-erase_internet
argv[2]=-kill_RIAA
argv[3]=-completely
argv[4]=-seriously
argv[5]=-but_leave_porn

The argv array and the argc number let your program control user input when calling it.

---

### Post by sirinabb on 2011-04-05
Thank you, this was exacly what i wanted to know :D

---

### Post by Daniel0108 on 2011-04-05
> **sirinabb said:**
> Thank you, this was exacly what i wanted to know :D

No problem, now please mark this thread as solved,

Daniel

---

### Post by sirinabb on 2011-04-05
done ;)

---

