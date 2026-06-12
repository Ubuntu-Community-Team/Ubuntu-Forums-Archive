---
title: "Weard Compile output"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by auroraa9420 on 2011-06-20
i tried to compile a simple opengl polygon code and i got this terrible output

what should i do????

/tmp/ccYURyEY.o: In function `InitGL':
main.c: (.text+0x1b) : undefined reference to `glClearColor'
main.c: (.text+0x28) : undefined reference to `glClearDepth'
main.c: (.text+0x32) : undefined reference to `glDepthFunc'
main.c: (.text+0x3c) : undefined reference to `glEnable'
main.c: (.text+0x46) : undefined reference to `glShadeModel'
main.c: (.text+0x50) : undefined reference to `glMatrixMode'
main.c: (.text+0x55) : undefined reference to `glLoadIdentity'
main.c: (.text+0x96) : undefined reference to `gluPerspective'
main.c: (.text+0xa0) : undefined reference to `glMatrixMode'
/tmp/ccYURyEY.o: In  function `ReSizeGLScene':
main.c: (.text+0xd6) : undefined reference to `glViewport'
main.c: (.text+0xe0) : undefined reference to `glMatrixMode'
main.c: (.text+0xe5) : undefined reference to `glLoadIdentity'
main.c: (.text+0x126) : undefined reference to `gluPerspective'
main.c: (.text+0x130) : undefined reference to `glMatrixMode'
/tmp/c cYURyEY.o: In function `DrawGLScene':
main.c: (.text+0x140) : undefined reference to `glClear'
main.c: (.text+0x145) : undefined reference to `glLoadIdentity'
main.c: (.text+0x15d) : undefined reference to `glTranslatef'
main.c: (.text+0x167) : undefined reference to `glBegin'
main.c: (.text+0x17a) : undefined reference to `glVertex3f'
main.c: (.text+0x192) : undefined reference to `glVertex3f'
main.c: (.text+0x1aa) : undefined reference to `glVertex3f'
main.c: (.text+0x1af) : undefined reference to `glEnd'
main.c: (.text+0x1c2) : undefined reference to `glTranslatef'
main.c: (.text+0x1cc) : undefined reference to `glBegin'
main.c: (.text+0x1e4) : undefined reference to `glVertex3f'
main.c: (.text+0x1fc) : undefined reference to `glVertex3f'
main.c: (.text+0x214) : undefined reference to `glVertex3f'
main.c: (.text+0x22c) : undefined reference to `glVertex3f'
main.c: (.text+0x231) : undefined reference to `glEnd'
main.c: (.text+0x236) : undefined reference to `glutSwapBuffers'
/tmp/ccYURyEY.o: In function `keyPressed':
main.c: (.text+0x268): undefined reference to `glutDestroyWindow'
/tmp/ccYURyEY.o: In function `main':
main.c: (.text+0x296) : undefined reference to `glutInit'
main.c: (.text+0x2a0) : undefined reference to `glutInitDisplayMode'
main.c: (.text+0x2af) : undefined reference to `glutInitWindowSize'
main.c: (.text+0x2be) : undefined reference to `glutInitWindowPosition'
main.c: (.text+0x2c8) : undefined reference to `glutCreateWindow'
main.c: (.text+0x2db) : undefined reference to `glutDisplayFunc'
main.c: (.text+0x2e0) : undefined reference to `glutFullScreen'
main.c: (.text+0x2ed) : undefined reference to `glutIdleFunc'
main.c: (.text+0x2f7) : undefined reference to `glutReshapeFunc'
main.c: (.text+0x301) : undefined reference to `glutKeyboardFunc'
main.c: (.text+0x315) : undefined reference to `glutMainLoop'

---

### Post by heyandy889 on 2011-06-20
Hey, dude. Looks like you forgot to include a library. Or, more precisely, you didn't "link" the library. I'm not sure what to do in your case, but let me describe a similar case.

I made a main.c looking like this

```
#include<stdio.h>
#include<math.h>
int main(){
	printf("sin(3.14159/2): %f\n",sin(3.14159/2));
	printf("cos(3.14159/2): %f\n",cos(3.14159/2));
	printf("tan(3.14159/2): %f\n",tan(3.14159/2));
	return 0;
}//end main()
```
Watch what happens when I try to compile this bad boy.
```
Script started on Mon 20 Jun 2011 07:52:23 PM EDT
**nrshiff@css09:~$ gcc test.c **
/tmp/ccUo7XPn.o: In function `main':
test.c:(.text+0xd): undefined reference to `sin'
test.c:(.text+0x29): undefined reference to `cos'
test.c:(.text+0x45): undefined reference to `tan'
collect2: ld returned 1 exit status
[B]nrshiff@css09:~$ gcc test.c -lm         <----- -lm is the key guy, right here.
nrshiff@css09:~$ ./a.out [/B]
sin(3.14159/2): 1.000000
cos(3.14159/2): 0.000001
tan(3.14159/2): 753695.995141        <---mathematically, tan(pi/2) gives "undefined"
**nrshiff@css09:~$ exit**
exit

Script done on Mon 20 Jun 2011 07:52:37 PM EDT
```
Anyways, what is the deal? Why did we get this funky error? Well, I wanted to use sin(), cos(), and tan() from within math.h. Unfortunately, when I went to compile the code using gcc, the C header file math.h was nowhere to be found. To fix this, I ran "gcc test.c -lm" to link the math library explicitly.

So, my guess is that you're including some header file that you need to link. Can you post the lines in your main.c that looks like the following?
```
#include blah/blah
#include blah/stuff
#include blah/morestuff
#include blah/stuff
#include blah/stuff
```

---

### Post by auroraa9420 on 2011-06-20
WoW THANKS A LOT :D

---

