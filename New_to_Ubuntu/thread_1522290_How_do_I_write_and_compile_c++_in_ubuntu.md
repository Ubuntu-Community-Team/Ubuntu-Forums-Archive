---
title: "How do I write and compile c++ in ubuntu?"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by tacotime on 2010-07-02
I've been trying all night, following various guides, i just want to make a basic hello world kind of script 

can y'all walk me through the process? 

Thanks in advance 


-Tacotime :popcorn:

---

### Post by akureikorineko on 2010-07-02
I forget what to write in the text editor, but just open up gedit or any other text editor, save the file as a .cpp file. When i started to learn how to program (dropped it for now) i compiled through the command line.

```
cd /to/your/file.cpp
g++ your file
./the new executable

```

---

### Post by krishnandu.sarkar on 2010-07-02
Ya good idea is to compile and run from Terminal rather than any IDE.

Ok....as akureikorineko said. It's same and as simple as that.

1. Write the program and save it as .cpp
2. g++ -o filename.cpp filename
3. ./filename

akureikorineko's way is also right. But remembering the file name is easy that's why I would suggest to change the output to filename by specifying -o with g++. Otherwise you can always use ./a.out which refers to the last executable.

---

### Post by akureikorineko on 2010-07-02
As I believe you can tell, I didn't stay with programming very long.

---

### Post by QIII on 2010-07-02
> **krishnandu.sarkar said:**
> Ya good idea is to compile and run from Terminal rather than any IDE.

Er, well, unless you do it for a living.  But maybe I'm wrong.  I dunno.  Maybe I've been doing it too long.

As an aid to learning from the ground up, I agree -- but that is only as an introduction. Rapid application development is a bit tough using Emacs and compiling from the cli.

---

### Post by artemyv on 2010-07-02
> **QIII said:**
> 

As an aid to learning from the ground up, I agree -- but that is only as an introduction. Rapid application development is a bit tough using Emacs and compiling from the cli.

Emacs could be configured to compile from menu and present the error list in the "bottom" window - where errors are clickable and bring the cursor to the correct line in source...


But I prefer CodeBlocks even for small "HelloWorld" samples...

---

### Post by marshmallow1304 on 2010-07-02
> **krishnandu.sarkar said:**
> 
2. g++ -o filename.cpp filename
3. ./filename


```
g++ -o filename filename.cc   (or .cpp)
./filename
```


As for IDEs, I'm rather fond of [Geany]("apt://geany").

---

### Post by slooksterpsv on 2010-07-02
Technically this is where bash becomes your friend, especially for linker jobs.

Here's what I do:

MKPROG="g++ -o myprog"

then all I have to do is type:

$MKPROG main.cpp

Or you could do this

MKPROG="g++ -o"

$MKPROG MyApp main.cpp

Isn't scripting fun =D

---

