---
title: "working with gnu g++"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by manish411 on 2010-07-28
i have downloaded gnu g++ package from ubuntu software center. but i dont know how to work with it.
I dont even know in wich folder this package is installed into .
plz help

---

### Post by earthpigg on 2010-07-28
are you talking about the gnu c compiler? 

it's manual can be read by entering 'man gcc' into a terminal.

---

### Post by vikas.sood on 2010-07-28
> **manish411 said:**
> i have downloaded gnu g++ package from ubuntu software center. but i dont know how to work with it.
I dont even know in wich folder this package is installed into .
plz help

Thats a GNU C++ compiler. You compile C++ code with it. If you installed using synaptic you dont need to worry about anything. 

type "which g++" in a terminal. it will tell you where your compiler is.

---

### Post by manish411 on 2010-07-28
i know that it is used to compile c++ programs . But what are the shell commands in order to do this

---

### Post by vikas.sood on 2010-07-28
> **manish411 said:**
> i know that it is used to compile c++ programs . But what are the shell commands in order to do this

You can call the compiler with g++ command to compile your code.

write your source file. eg mySourceFile.cpp

g++ -o <executable-name> mySourceFile.cpp

You can see the man page for more options and switches. for eg. -g to include debug information, -I for include file paths. etc.

Go through the man page for more.

---

### Post by manish411 on 2010-07-28
can you please elaborate on this as I am a beginner . What I ve already done is downloaded g++ 4.4.
Now i dont know what to do next. in which folder to write the source code? where are the commands located, and how to set the path ?

---

### Post by davidmohammed on 2010-07-28
how about [this]("http://talkbinary.com/programming/c/how-to-write-and-compile-c-program-in-linux/") for a step by step guide?

---

### Post by manish411 on 2010-07-28
i tried all the steps but my command g++ is not working .it says that the command g++ can be found in some other packages. do we have to set up a path for the command so  that the shell 
finds it.

---

### Post by da burger on 2010-07-28
How did you download g++? Did you get it from synaptic or did you download a tar.gz file from the internet? Or something else?

Angus

---

### Post by sheldon1 on 2010-07-28
First,  need to make sure that you've installed g++ correctly. Did you download a .tar.gz file (or something similar, like a .zip file)? If you did, let us know because g++ isn't installed automatically simply from downloading those files. 

Try running in Terminal ( Applications -> Accessories -> Terminal)

sudo apt-get install 

Then, type in your password (same as the one used for login). It will ask if you want to install the package and use the additional disk space. Answer yes. Then, it should install no problem.

After that, try a Google search for g++ commands. 

Or, check out this book; it is super handy. It goes over the most important g++ commands, and has TONS of other really, really valuable information in it. I use it all the time.

[http://www.amazon.com/Linux-Pocket-Guide-Daniel-Barrett/dp/0596006284/ref=sr_1_3?ie=UTF8&s=books&qid=1280342096&sr=8-3-spell](http://www.amazon.com/Linux-Pocket-Guide-Daniel-Barrett/dp/0596006284/ref=sr_1_3?ie=UTF8&s=books&qid=1280342096&sr=8-3-spell)


-sheldon

---

### Post by vikas.sood on 2010-07-28
> **manish411 said:**
> can you please elaborate on this as I am a beginner . What I ve already done is downloaded g++ 4.4.
Now i dont know what to do next. in which folder to write the source code? where are the commands located, and how to set the path ?

How did you download g++? I would suggest you to use synaptic or apt-get install.
you can use following command in a terminal. make sure you are connected to internet before that.
```
sudo apt-get install g++
``` 

Once done, you dont need to do anything. you are good to compile your code.

In case you still have problems, paste the output of following commands.

which g++
echo $PATH

---

### Post by manish411 on 2010-07-29
i tried this also and it asked for the password also but after that it does not install anything

---

