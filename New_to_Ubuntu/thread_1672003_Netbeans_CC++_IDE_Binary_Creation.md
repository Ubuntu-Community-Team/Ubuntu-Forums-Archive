---
title: "Netbeans C/C++ IDE Binary Creation"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by satyanash on 2011-01-20
Hello,
I installed Netbeans 6.9.1 and created a sample C program, i was able to build it successfully and run it too. Also the program works well and gives the desired output, but i just cant seem to find an option to create a binary file like the one created when manually using gcc to compile a c program created in gedit. 

How can i make a binary executable file like the one with .out extension in gcc.

Satyajeet

---

### Post by satyanash on 2011-01-23
bump..

---

### Post by bouncingwilf on 2011-01-23
Unless you're using any additional libraries then;
gcc -o myfile myfile.c 

should be sufficient to produce an executable called myfile

./myfile to execute.

Bouncingwilf

---

### Post by santosh83 on 2011-01-23
> **sattu94@gmail.com said:**
> Hello,
I installed Netbeans 6.9.1 and created a sample C program, i was able to build it successfully and run it too. Also the program works well and gives the desired output, but i just cant seem to find an option to create a binary file like the one created when manually using gcc to compile a c program created in gedit. 

How can i make a binary executable file like the one with .out extension in gcc.

Satyajeet

Simple. Just rename the executable created by Netbeans to a.out!

Seriously, is there a reason why you need to do this? The a.out file created by gcc and the one created by Netbeans (which relies on gcc for the backend) are likely almost identical. It's only the file names that differ.

---

### Post by satyanash on 2011-01-23
> **bouncingwilf said:**
> Unless you're using any additional libraries then;
gcc -o myfile myfile.c 

should be sufficient to produce an executable called myfile

./myfile to execute.

Bouncingwilf

> **santosh83 said:**
> Simple. Just rename the executable created by Netbeans to a.out!

Seriously, is there a reason why you need to do this? The a.out file created by gcc and the one created by Netbeans (which relies on gcc for the backend) are likely almost identical. It's only the file names that differ.

I think you have misunderstood me, i meant i wanted to create a standalone binary executable just like the one gcc creates but through netbeans.. netbeans only has the option to build an entire project.

File name is not important i just used the a.out name for reference.
The compile single file option does compile it but does it produce an executable binary ?
If it does, where ?

Satyajeet:popcorn:

---

### Post by bouncingwilf on 2011-01-23
Apologies for the misunderstanding. I use Code::blocks myself but the usual practice is for the ide to generate a new directory for each project  and often a subdirectory under that to hold the executable ( usually they are named bin or debug or something like that). If Netbeans has sucessfully compiled then the execuable will be there somewhere! Often these files are in "hidden" folders so go to places-> home and then type ctrl-H (to see hidden files/directories) and try and follow either the Netbeans folder or your project name trails. It will be there somewhere! If that fails, use Places-> search for files and be sure to ensure it searches for hidden files.


Bouncingwilf

---

### Post by santosh83 on 2011-01-23
> **sattu94@gmail.com said:**
> I think you have misunderstood me, i meant i wanted to create a standalone binary executable just like the one gcc creates but through netbeans.. netbeans only has the option to build an entire project.

File name is not important i just used the a.out name for reference.
The compile single file option does compile it but does it produce an executable binary ?
If it does, where ?

Satyajeet:popcorn:

If you just want to compile one source file into the corresponding executable without all the support files that most IDEs necessarily create, then the way to go is to just use gcc directly from the command-line. This is fine for all single source file projects, and even for small projects of a handful of source files. Makefiles and IDEs are really helpful when compiling larger projects with dozens of source files and complicated dependencies, IMO.

---

### Post by satyanash on 2011-01-23
> **bouncingwilf said:**
> Apologies for the misunderstanding. I use Code::blocks myself but the usual practice is for the ide to generate a new directory for each project  and often a subdirectory under that to hold the executable ( usually they are named bin or debug or something like that). If Netbeans has sucessfully compiled then the execuable will be there somewhere! Often these files are in "hidden" folders so go to places-> home and then type ctrl-H (to see hidden files/directories) and try and follow either the Netbeans folder or your project name trails. It will be there somewhere! If that fails, use Places-> search for files and be sure to ensure it searches for hidden files.


Bouncingwilf


I seem to have found the file, it has a .o extension.
But i cannot execute it. I tried chmod +x but still it wont run. I also have found the source file.
I know i can compile the source file using GCC. But i want to do it through Netbeans because i don't want to go gcc it all the time. So you know just an option to save an executable binary file for your current source file would be nice. If there is something like that.

I also was recently considering which IDE to use i was going to download Eclipse but since Netbeans was smaller, i decided to do it. Is Eclipse any better?

Satyajeet
Thank You for the replies.:popcorn:

---

### Post by santosh83 on 2011-01-23
> **sattu94@gmail.com said:**
> I seem to have found the file, it has a .o extension.
But i cannot execute it. I tried chmod +x but still it wont run. 
Satyajeet
Thank You for the replies.:popcorn:

Files ending in *.o or *.so are so-called object files. While they contain the object code for the source code you've written, they cannot run as such, since they do not contain the object code for external functions that you may have called in your source, like say printf(). You need to link the object file with all the libraries it depends on (in Unix systems, this step is done by the **ld** linker) to produce a complete executable, which usually has no filename extension in Unix, to run your program.

> gcc -o file file.o

will perform the linking for the .o file. If you've more than one .o file, supply them all to gcc.

---

### Post by satyanash on 2011-01-23
> **santosh83 said:**
> Files ending in *.o or *.so are so-called object files. While they contain the object code for the source code you've written, they cannot run as such, since they do not contain the object code for external functions that you may have called in your source, like say printf(). You need to link the object file with all the libraries it depends on (in Unix systems, this step is done by the **ld** linker) to produce a complete executable, which usually has no filename extension in Unix, to run your program.



will perform the linking for the .o file. If you've more than one .o file, supply them all to gcc.

Yes this works. But again i have to go the GCC way. and according to bouncingwilf the file should already be an executable. Hmm.. i think i will have to just do it manually.

Okay but when i build an entire project succesfully( that contains only one program), how do i run it?
That is without netbeans.

Satyajeet:popcorn:

---

### Post by santosh83 on 2011-01-23
> **sattu94@gmail.com said:**
> Yes this works. But again i have to go the GCC way. and according to bouncingwilf the file should already be an executable. Hmm.. i think i will have to just do it manually.

Okay but when i build an entire project succesfully( that contains only one program), how do i run it?
That is without netbeans.

Satyajeet:popcorn:

Just invoke the executable from the command-line. If you built the project with Netbeans, go into the appropriate build folder, or else wherever gcc placed the executable and do:

```
./my_program
```

---

### Post by bouncingwilf on 2011-01-23
> **sattu94@gmail.com said:**
> Yes this works. But again i have to go the GCC way. and according to bouncingwilf the file should already be an executable. Hmm.. i think i will have to just do it manually.

Okay but when i build an entire project succesfully( that contains only one program), how do i run it?
That is without netbeans.

Satyajeet:popcorn:
If you found the object file and you can run an executable generated by netbeans then the Netbeans generated file must exist! - it won't be far away! I suggest you have another look - the project setup in Netbeans should tell you where it stores them.

Bouncingwilf

---

### Post by satyanash on 2011-01-23
> **bouncingwilf said:**
> If you found the object file and you can run an executable generated by netbeans then the Netbeans generated file must exist! - it won't be far away! I suggest you have another look - the project setup in Netbeans should tell you where it stores them.

Bouncingwilf

There is one other file with a .o.d extension and same file name. And where is project setup ?
Satyajeet

---

### Post by brianpesda on 2011-02-14
try:
~/NetBeansProjects/YourProjectName/dist/Debug/GNU-Linux-X86/YourProjectName

or:
~/NetBeansProjects/YourProjectName/dist/Release/GNU-Linux-X86/YourProjectName

for your executable...

Brian

---

