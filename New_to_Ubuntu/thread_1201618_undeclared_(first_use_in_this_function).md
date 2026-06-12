---
title: "undeclared (first use in this function)"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by shaheru on 2009-07-01
Hello,
I try to install a programme that I put in username/software.
After untar it, I lauch a Make programme from the newly created dir using 

make -f Makemdx_g77

I receive then a series of error messages as

graphx_mdx.c:2681: error: expected declaration specifiers before ‘Widget’
graphx_mdx.c:2682: error: expected declaration specifiers before ‘Pixmap’
graphx_mdx.c:2683: error: expected declaration specifiers before XmAnyCallbackStruct’
...
or 
...
graphx_mdx.c:2606: error: ‘fgx’ undeclared (first use in this function)
graphx_mdx.c:2609: error: ‘lgx’ undeclared (first use in this function)
graphx_mdx.c:2620: error: ‘xswa’ undeclared (first use in this function)
...

therefore the programme is not installed. Something is missing but I don' t really know where I have to look for.

If I open the Makemdx_g77, the first lines are:

----------------------------
FC = g77
# FFLAGS = -DM10 -ffixed-line-length-none  -O
FFLAGS = -DM10 -DIO64 -ffixed-line-length-none  

CC = gcc 
# CFLAGS = -DM10 -O 
CFLAGS = -DM10 -DIO64

XINC = -I/usr/**X11R6/include/** -I/sw/include/
XLIB =  -L/sw/lib  -lXm -L/usr/**X11R6/lib** -lXt -lX11
LIB = -lm  

LC = g77

XTARGS = mdx
  
all: $(XTARGS) 

graphx_mdx.o : graphx_mdx.c

etc...
--------------------------------
In bold some dir that I don' t have,
what I have is only /usr/X11R6/**bin**

nothing related to "include" or "lib"

I don't know if this is related to these error messages,


Thanks for helping!

---

### Post by carml on 2009-07-01
Can you go to Applications->Accessories->Terminal and post here the result of ```
sudo apt-get install build-essential
``` you'll be prompted to insert your password.

---

### Post by shaheru on 2009-07-01
Hello, I did so and then rerun the Make file but there is still the same error messages.

valerio@valerio:~$ sudo apt-get install build-essential
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Lettura delle informazioni di stato... Fatto     
build-essential è già alla versione più recente.
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.

 ..it is in italian but it seems that it was already updated!

---

### Post by shaheru on 2009-07-02
Solved.
This programme need to have lesstif installed and I didn' t pay attention to install also lesstif -dev

---

