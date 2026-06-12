---
title: "Compiling C++ in Ubuntu"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by DeLaney on 2009-01-25
I've learned a small bit of C++ in Windows, but coming to Linux I have no idea how to compile programs, or if I should be writing them in anything specific. Also, the book I have tells me that I'll get an EXE. file after using a compiler. How will this work in Ubuntu?

---

### Post by igknighted on 2009-01-25
> **DeLaney said:**
> I've learned a small bit of C++ in Windows, but coming to Linux I have no idea how to compile programs, or if I should be writing them in anything specific. Also, the book I have tells me that I'll get an EXE. file after using a compiler. How will this work in Ubuntu?

install the package 'build-essential', then use the command 'g++' to compile.  If you were using Cygwin and GCC in windows, it will be exactly the same, aside from the filename of the output.  In windows, you get a.exe, while in linux you get a.out (unless you use the -o flag to manually set the name).  To run the program, type './a.out'.

---

### Post by DeLaney on 2009-01-25
Cool, thanks. 

I have the build-essential package, and I've tried using the g++ command to compile, I'm unsure how. I tried putting g++ and then the path to the file directory, and it said; 

g++: home/zack/Game_Programming/Hello: No such file or directory
g++: no input files

Is there something else I have to put before the directory or file?

---

### Post by sylvainrb on 2009-01-25
Make sure that you are compiling a .cpp file. Here's what I use to compile and run:
```
g++ filename.cpp -o name
./name
```

---

### Post by igknighted on 2009-01-25
> **DeLaney said:**
> Cool, thanks. 

I have the build-essential package, and I've tried using the g++ command to compile, I'm unsure how. I tried putting g++ and then the path to the file directory, and it said; 

g++: home/zack/Game_Programming/Hello: No such file or directory
g++: no input files

Is there something else I have to put before the directory or file?

If you are going to use the full path to the file, it needs to start with a "/".  It appears the command you should be using (by the path posted above): "g++ /home/zach/Game_Programming/Hello".  Also, you should end c++ source files with .cpp or .cc.

---

### Post by DeLaney on 2009-01-26
Awesome, thanks! It works now, it's just giving me error messages on bad code, which I can deal with. Thank you! 

Well, I fixed up the code, and it compiled into a .out file, but I can't seem to open it. Is there a specific program I need?

---

### Post by snova on 2009-01-26
> **DeLaney said:**
> Awesome, thanks! It works now, it's just giving me error messages on bad code, which I can deal with. Thank you! 

Well, I fixed up the code, and it compiled into a .out file, but I can't seem to open it. Is there a specific program I need?

"Open" it? If you're clicking on it, anything it reads/writes from the terminal will go off into nothingness. You need to run it from a terminal. One will not be created automatically.

If you're already trying to run it from a terminal, what precise command are you using?

---

### Post by DeLaney on 2009-01-26
Ah... I had no idea that I was supposed to run my programs from the terminal as well. How would I do that?

---

### Post by Sealbhach on 2009-01-26
> **DeLaney said:**
> Ah... I had no idea that I was supposed to run my programs from the terminal as well. How would I do that?

To run any app, just type its name in the terminal. Try it with "firefox".


.

---

### Post by Strohfeuer on 2009-01-26
my 2 cents ;)

[http://ubuntuforums.org/showthread.php?p=6609233#post6609233]("http://ubuntuforums.org/showthread.php?p=6609233#post6609233")

---

### Post by mrbiggbrain on 2009-01-26
> **Sealbhach said:**
> To run any app, just type its name in the terminal. Try it with "firefox".


.

but firefox has a symbolic link that makes firefox point to somewhere. this is NOT the case for files you compile yourself

do 

```
#./file-name
```

where . is the directory the program is in. you can feel free to name files whatever you please, as unlike windows, linux does not determine if a file is execuble based upon its extention (.exe, .com)

---

### Post by DeLaney on 2009-01-26
Alright, thanks guys! I managed to get it to run, so I think I should be set. Thanks for the tip on other editor too, I'll give it a shot with my next program.

---

### Post by matthew.ball on 2009-01-27
Geany and Kate (are two editors I know of), which include a terminal in a text-editor environment (might even be possible to set-up a compiler for either, I don't know).

Unless you don't mind running a terminal with your text-editor, it's just useful to have it all in the one application in my experience.

---

