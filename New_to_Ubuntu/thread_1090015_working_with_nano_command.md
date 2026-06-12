---
title: "working with nano command"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by amrutayan on 2009-03-07
thanks for the help regarding my previous posts....

any way i get confused using command nano....

my aim is just to write a** shell script or a c program **

than save it and run it.

but i am confused using nano or pico command that after writing a c program how i can properly save it??

i am confused with the command

so plz tell me the command  procedure to save my program and later to execute it.

---

### Post by taurus on 2009-03-07
<Ctrl>x

^X Exit means hold down the <Ctrl> while pressing x.

---

### Post by ekaqu on 2009-03-07
> **amrutayan said:**
> 
so plz tell me the command  procedure to save my program and later to execute it.

ctrol + x will exit, if the file has been updated at all, it will ask if you want to save (hit yes).

after that it puts you back on the terminal.  

lets say the file is called a.  To execute the file you will need to change the settings of the file.

```
chmod a+x a 
```  
this makes it executable.

if you wrote a c program, use gcc a -o programname

to execute the files, type ./<name> where name is the name of the file.

---

### Post by matthew.ball on 2009-03-07
When using nano, it's probably more comfortable to use Ctrl+Z to "suspend" exit, rather than a Ctrl+X exit.

With Ctrl+Z the nano process is suspended to the background, returning you to your default terminal window - where you can use gcc, etc.

You can easily return to your nano session by simply typing fg in the terminal.

Edit: Ctrl+Z won't ask you to save the file (after all, you're not really closing it), so Ctrl+O (the letter o) to save before doing a Ctrl+Z.

---

