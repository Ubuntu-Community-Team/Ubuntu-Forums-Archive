---
title: "Executable not opening"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by WBojangles on 2010-12-24
Hello,

I wrote a small test program in C++, compiled and it works starting from the terminal. I tried to open it by launching it like any other program, but nothing came up. It shouldn't be a problem of opening and closing because it only prints one line or something, there is interaction (input from user). Do I have to tell it to open by means of the terminal (not going into terminal and typing "./test"), and if so how?

---

### Post by davidmohammed on 2010-12-24
I presume the launcher you have created you have set its properties - permissions to have "execute" permissions?

---

### Post by WBojangles on 2010-12-26
Ok the executable flag is ticked, but it still refuses to open when I execute it from the folder. Nothing comes up, it just acts as if I never did any action.

---

### Post by davidmohammed on 2010-12-26
... and the exe itself is executable?

chmod +x <name of exe>

---

### Post by fslezak on 2010-12-26
Executables usually cannot be run from the folder.

What is the file extension? I may be able to make you a SH file that can run the C++ file.

---

### Post by fslezak on 2010-12-26
Executables usually cannot be run from the folder.

What is the file extension? I may be able to make you a SH file that can run the C++ file.

---

### Post by cmcanulty on 2010-12-26
OK I was just reading this thread and can you explain how to run executables if not from folder?

---

### Post by mcduck on 2010-12-26
> **WBojangles said:**
> Hello,

I wrote a small test program in C++, compiled and it works starting from the terminal. I tried to open it by launching it like any other program, but nothing came up. It shouldn't be a problem of opening and closing because it only prints one line or something, there is interaction (input from user). Do I have to tell it to open by means of the terminal (not going into terminal and typing "./test"), and if so how?

If you don't tell the launcher to run your program in a terminal, it won't do that. It will simply run the program in the background.

When creating a launcher, there's a dropdown box allowing you to set the launcher type. Try setting that to "Application in Terminal".

Note that this way the terminal will close automatically as soon as the application finishes execution. If you want the terminal window to stay open, for example to be able to read any final output from your application, you should instead create a script to run the application and point the launcher to the script.

For example you could use something like this:
```
#bin/bash
/path/to/yourexecutable
read
exit
```
(the "read" command, when used alone, will pause the script until the user presses any key)

Edit:
I just realized that you aren't even using a launcher. That's probably not going to work unless you make your program to draw a window for itself. It's running just fine and doing what it's supposed to do, but without anything to output to... You'll have to eithr create a startup script or a launcher that starts your program in a terminal or redirects it's output into a window.

---

### Post by WBojangles on 2010-12-26
Ok, I made a launcher that opens it in terminal (for those who might be in a similar situation, while creating a launcher on a panel, I changed the dropdown "Type" from "Application" to "Application in Terminal") - thanks for that tip. This actually works out very well for a program that I want to be able to launch easily anyway, but it might be a bit overkill for running a really small test program.

In case I am being unclear, I am wondering if it is possible to tell the application itself to open in terminal without manually programming that or making a launcher. If the only way to do it would be programming or a long workaround, then it's not a big problem, I can still run it from terminal like before ("./[program name]").

---

