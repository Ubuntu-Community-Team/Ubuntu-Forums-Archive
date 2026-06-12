---
title: "Store the Compilation Error"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by raj_rahul26 on 2009-11-09
[B]Hi Guys,

           I am new to this forum and this is my first post.I just compiled a .c file(command prompt) with compilation errors.Can anyone tell me how to store the compilation error in the text file or else is there any command to just view the compilation errors.Thank You.[/B]):P

---

### Post by jbrown96 on 2009-11-09
It should print the errors to the console. What command are you using to compile it? You could redirect the console output to a file with ```
gcc SOURCE.c 2&> file.txt
``` that will store everything to file.txt in the current directory.

---

### Post by raj_rahul26 on 2009-11-09
Thanks for the reply will just update you within few minutes.Thank You.

---

### Post by raj_rahul26 on 2009-11-10
**Well,Thanks a lot for your reply it worked I am able to store the compilation error in a particular file.I did it as you said but with the command : gcc source.c 2&> file.txt when i opened the file.txt i had got this error first gcc: 2 : No such file or directory than i did the compilation without 2 like this gcc source.c &> file.txt, it worked out.Thanks.**:D:D:D

---

### Post by jbrown96 on 2009-11-10
There are two standout outputs in Linux. the first is stdout and second is stderr. Without the 2, then just stdout is added to the file. Gcc might not use stderr, which is why it would complain. Most other programs do, so if you every need to store output from stout and stderr and some of it is missing, it's becasue you need to do 2&>

---

