---
title: "editing in terminal problem"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by amrutayan on 2009-03-07
i am new to ubuntu....

i have just created a file by

$cat>a [enter]
abcde
asdf
asdff

line5

but my prob over here is that fter i have came to "line5" i am unable to back into previous line ............when i try UPARROW to go up it show me sign like "^[[A"
and i am unable to go to previous line by mouse click or back space.

so any one help me regarding my issue.....

thanks

---

### Post by ekaqu on 2009-03-07
cat has yet to see a stop command.

so after you type 
"abcde
asdf
asdff

line5"

hit enter then do one of the next 3 things.
ctrl + z
ctrl + d
ctrl + c

All will stop and get you back into the command line.

---

### Post by ekaqu on 2009-03-07
Also if you want a generic way to edit and make files in the terminal there are several programs that are nice and easy to use but for starting out I would say use pico. The commands are displayed on the screen for you with things like:  ^X exit 

this means hit ctrl + x to exit (will prompt to save if you changed anything).

So for your file, type  pico a
once the program opens up in the terminal, just type like any normal text editor. then use the options on the lower part of the screen to do what you need (like exit and save).

---

### Post by Rolcol on 2009-03-07
> **ekaqu said:**
> Also if you want a generic way to edit and make files in the terminal there are several programs that are nice and easy to use but for starting out I would say use pico. The commands are displayed on the screen for you with things like:  ^X exit 

this means hit ctrl + x to exit (will prompt to save if you changed anything).

So for your file, type  **pico** a
once the program opens up in the terminal, just type like any normal text editor. then use the options on the lower part of the screen to do what you need (like exit and save).

In Ubuntu, pico points to nano which is the command I suggested in your other thread.

---

