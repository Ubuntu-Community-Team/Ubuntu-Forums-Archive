---
title: "Linux commands"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by ebeute on 2011-03-05
Hi, I am student taking an operating system class. For my assignment, I am given a program that the professor wants me to run and analyze what is going on with it. My questions is how to do I open the file so that I can run it? Does anyone know?

---

### Post by TeoBigusGeekus on 2011-03-05
What's the program? Is it a script or an executable?
What's its name?

---

### Post by dFlyer on 2011-03-05
> **ebeute said:**
> Hi, I am student taking an operating system class. For my assignment, I am given a program that the professor wants me to run and analyze what is going on with it. My questions is how to do I open the file so that I can run it? Does anyone know?

What is the file name with extension if it has one.

---

### Post by Locke_99GS on 2011-03-05
Change directory to where the program is located:
*cd /home/ebeute/programfolder*

If it is a precompiled binary, (or a bash script) make sure it is marked executable:
*chmod +x myprogram*

Then just run it from current directory:
*./myprogram*

---

### Post by Rinzwind on 2011-03-05
> **ebeute said:**
> Hi, I am student taking an operating system class. For my assignment, I am given a program that the professor wants me to run and analyze what is going on with it. My questions is how to do I open the file so that I can run it? Does anyone know?


Go to command line.
cd to_directory_that_has_file
file {filename}
if it says "text" you can use gedit 
gedit {filename}

otherwise post what is says after you issue the file command and someone will tell you.

If it is a text file that has commands you can make the file executable by doing
chmod 775 {filename}
or
chmod +x {filename}
and then
./{filename}

---

### Post by ebeute on 2011-03-05
Hi,


This is part of the instructions of the assignment:  I am basically given a program that just needs to be compiled. See the instructions that my teacher gave verbatim.

Thanks 

[LIST]
[*][FONT=Times New Roman]Write the following programs as explained below. Show how to compile and run the programs by typescript [/FONT][FONT=Comic Sans MS]($script outfile[/FONT][FONT=Times New Roman]) including source program listings (e.g., [/FONT][FONT=Comic Sans MS]$cat –n prog.c[/FONT][FONT=Times New Roman]). [/FONT]
[/LIST] 
 
My problems is that I have saved the program and now I don't know how to open it up so that I can run it.

Thanks

 
> **TeoBigusGeekus said:**
> What's the program? Is it a script or an executable?
What's its name?

---

### Post by ebeute on 2011-03-05
Ok below are part of the instructions that the professor gave me. The file name is fork.c

1) click on terminal 

2.) type in gedit  fork.c  \\ this is to set up the file

3.) my directory is cd cmp426 is this the correct way to type this in to the computer 

4.) gcc fork.c -ofork \\ Creates an exeutable file 
 
5.) ./fork  // runs the program

I think I'm missing a step because I have tried these steps. Can you write out a quick example process for me based on the file name that I just gave you. Note I really apreciate this because I don't know anything about unix.

Thanks 
 
 
 
> **Rinzwind said:**
> Go to command line.
cd to_directory_that_has_file
file {filename}
if it says "text" you can use gedit 
gedit {filename}
 
otherwise post what is says after you issue the file command and someone will tell you.
 
If it is a text file that has commands you can make the file executable by doing
chmod 775 {filename}
or
chmod +x {filename}
and then
./{filename}

---

### Post by rburkartjo on 2011-03-05
ebe if it is an installed program open a terminal ctrl + alt + the letter t. then type in the command to run the program followed space & and the word exit. what this does is start the command from the terminal and then close the terminal. for instance vlc & exit.

---

