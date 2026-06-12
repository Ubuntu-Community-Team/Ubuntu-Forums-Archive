---
title: "please help"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by shishir_knit on 2009-03-17
I m a newbie on linux 
i want to execute a shell script(a .sh file)from a C program
how could i do it.which ide is most suitable for doing such operations.

also what is the substitute of .dll of windows in linux.

---

### Post by albandy on 2009-03-17
with the command system
for example:

#include <stdio.h>
int main()
{
printf("This will execute ls command");
system("ls");
}

---

### Post by shishir_knit on 2009-03-17
i want to execute a whole shell script

---

### Post by bobbob1016 on 2009-03-17
Open a terminal and type:
./name-of-script.sh or sh name-of-script.sh not 100% sure which.

IIRC there is no .dll equivalent in Linux.  Basically instead of comparing apples and oranges, you're comparing apples and potatoes, and asking where the potato seeds are.

---

### Post by shishir_knit on 2009-03-17
i wan to execute shell script through C program

---

### Post by shishir_knit on 2009-03-17
i m waiting
please reply

---

### Post by albandy on 2009-03-17
have you added execution perms to the script?

without execution perms: System("bash -c script.sh");
with execution perms: System("script.sh");


Ensure to add the path, for example: if the script is in your home /home/username/script.sh

System("/home/username/script.sh")

---

### Post by bobbob1016 on 2009-03-17
Don't repost or bump so often.  Bumping is when you post something that doesn't add information, just to get back to the top of the forum list again.

[http://www.linuxforums.org/forum/linux-programming-scripting/116520-how-execute-script-file-unside-c-program.html](http://www.linuxforums.org/forum/linux-programming-scripting/116520-how-execute-script-file-unside-c-program.html)
I googled 'run linux script in "c program"'

---

