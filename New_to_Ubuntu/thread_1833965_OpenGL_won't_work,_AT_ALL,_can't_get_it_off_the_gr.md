---
title: "OpenGL won't work, AT ALL, can't get it off the ground"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by cheeseits on 2011-08-26
So I think I've installed opengl and the stuff I need to make it work like glut and mesa.  I've also downloaded the beginner files from the opengl redbook.  At the command prompt I type and get:

```

'username'@'username'-laptop:~/Documents/C/openglbk$ gcc hello.c -o hello -lglut
hello.c:102: error: stray ‘\32’ in program

```Note, this is the exact file downloaded from the redbook.

What does this error mean????????  And how would I go about fixing it?
I've been to several sites to help me install opengl, none of the instructions work.

Thanks.

---

### Post by CatKiller on 2011-08-26
What are you trying to do?

---

### Post by cheeseits on 2011-08-27
I'm trying to run the simplest possible program with calls to openGL.  In doing so I'm specifically trying to run the program hello.c from the website:

 [http://opengl-redbook.com/source/OpenGL-1.4.zip](http://opengl-redbook.com/source/OpenGL-1.4.zip)


However when I try to run it, it gives me the error shown above.  Does that make sense??  I just want to run the file and have it display the graphics and not end in an error.

Thanks.

---

### Post by jacobsallan on 2011-08-27
It's not you.

$ gcc hello.c -o hello -lglut
hello.c:102:1: error: stray ‘\32’ in program

There really is a stray ASCII SUB in the file.
$ od hello.c |tail -2
0006640 027164 025040 006457 076412 005015 000032
0006653

I fixed it by deleting the last line with vi and then retyping the last line (so that it contains only a '}'.

$ tail -2 hello.c
   return 0;   /* ANSI C requires main to return int. */
}
$ gcc hello.c -o hello -lglut
$ ./hello

---

### Post by cheeseits on 2011-08-27
Thank you!  hello.c now runs.  I guess now I'll attempt to write a  script to remove the last chars from all the files...  Why in the world  are those in there anyways??

Ok, so I just now manually removed the stray stub from cube.c and image.c, when I run it, I get an error.

$ gcc cube.c -o cube -lglut
/tmp/ccSj8af7.o: In function `display':
cube.c: (.text+0xac): undefined reference to `gluLookAt'
collect2: ld returned 1 exit status

Similarly with image.c

$ gcc image.c -o image -lglut
/tmp/ccB5dblH.o: In function `reshape':
image.c: (.text+0x1e1): undefined reference to `gluOrtho2D'
collect2: ld returned 1 exit status

However hello.c does work.

Does this mean that I'm missing some kind of library or something???

---

