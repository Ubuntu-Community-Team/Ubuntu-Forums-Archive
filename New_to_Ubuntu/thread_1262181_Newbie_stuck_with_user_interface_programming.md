---
title: "Newbie stuck with user interface programming"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by megane16v on 2009-09-09
Let's try this way...

I'm new to Unix
I WANT to learn more of it.

Where is my problem?

I'm stuck with Xlib and X11

How do i make simple "hello world"program using X11?

I've seen examples on internet,but where do I make that example(in text editor,terminal?) and how can i see results of my programming? Thanks,hope u would help,because i don't know who will if you can't!

---

### Post by NoaHall on 2009-09-09
Using X11? You mean using a terminal. Just do 
```

echo Hello world!

```

---

### Post by megane16v on 2009-09-09
I'm not that lucky. It's not that simple. I know some bacis,including echo in terminal. But this is different.

My program needs to be simple _window_ program with one button that changes text "Hello world" to lets say "Hello Kitty".

---

### Post by NoaHall on 2009-09-09
Copy and paste into gedit, save, then do
chmod +x filename
```
#!/bin/bash
           OPTIONS="Hello_Kitty Hello_world"
           select opt in $OPTIONS; do
               if [ "$opt" = "Hello_Kitty" ]; then
                echo Hello Kitty
                exit
               elif [ "$opt" = "Hello_World" ]; then
                echo Hello World
               else
                clear
                echo Number one or two
               fi
           done

```

Options = What is displayed for the user to select from
$opt = Gets input from user, links it to the OPTIONS
If = If something then something
; = Terminator. Like with php and perl.
Else = if none of the "if" or "elif" things are fulfilled, then do this.
Done = end.

---

### Post by overdrank on 2009-09-09
Is this still homework? Maybe just link some good tutorials. :)

---

### Post by NoaHall on 2009-09-09
Okay, so the scripting you want is either Bash or Perl.
You can find sites.

I'd download geany for writing things.

---

### Post by megane16v on 2009-09-09
> **overdrank said:**
> Is this still homework? Maybe just link some good tutorials. :)

I would appriciate if somebody wold tell me where can I find,or what I have to read to start X Windows programing. What programs do I have to use,to make,compile such programs?

I have much to learn. OMG :confused:

---

### Post by NoaHall on 2009-09-09
You don't have to use any programs but a text editor. You don't need to compile, but every Bash file should begin with
"#!/bin/bash"
Then you need to enabled it be run as a program using "chmod +x /home/username/filename".
You can then run by using "/home/username/filename"

Try this site - [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html#toc10](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html#toc10)
And maybe this - [http://www.linuxheadquarters.com/howto/programming/glade.shtml](http://www.linuxheadquarters.com/howto/programming/glade.shtml)

---

### Post by megane16v on 2009-09-09
Well thank you NoaHall,but we didn't understood each other. Here is what i need. Something like in this picutre:

[IMG]http://img141.imageshack.us/img141/3030/79191223.png[/IMG]

And code is looking something like this:

#include <stdio.h>
#include <X11/Intrinsic.h>
#include <X11/StringDefs.h>
#include <X11/Xaw/Command.h>
#include <X11/Xaw/Form.h>
#include <X11/Xaw/Box.h>
    exit the program */
/*
static void exitHandler(Widget w, XtPointer callData, XtPointer clientData)
  {
  exit(0);
  }
/* print "hello" to stdout */
static void helloHandler(Widget w, XtPointer callData, XtPointer clientData)
  {
  printf("Hello\n");
  }
/* main program */
void main(int argc, char **argv)
  {
  XtAppContext appContext;
  Widget toplevel, box, topLabel, bottomPanel, helloButton, exitButton;
  toplevel = XtVaAppInitialize(&appContext, "AthenaDemo", NULL, 0, &argc, argv, NULL, NUL
  box = XtVaCreateManagedWidget("box",boxWidgetClass,toplevel,NULL);
  topLabel = XtVaCreateManagedWidget("topLabel", labelWidgetClass, box,
     XtNlabel," Pick One ",
     XtNborderWidth, 0,
     NULL);
  bottomPanel = XtVaCreateManagedWidget("bottomPanel", formWidget-
Class, box,
XtNsensitive, True,
XtNborderWidth, 0,
NULL);
  helloButton = XtVaCreateManagedWidget("helloButton", commandWid-
getClass, bottomPanel,
                               18
XtNlabel," Hello ",
NULL);
  XtAddCallback(helloButton, XtNcallback, helloHandler, NULL);
  exitButton = XtVaCreateManagedWidget("exitButton", commandWid-
getClass, bottomPanel,
       XtNlabel," Exit ",
       XtNfromHoriz,helloButton,
       NULL);
  XtAddCallback(exitButton, XtNcallback, exitHandler, NULL);
  XtRealizeWidget(toplevel);
  XtAppMainLoop(appContext);
  }


So guy's ,how can i make this programm,and what do i need to have installed to run it,where is this program writen? gedit? emacs? So many questions,OMG!

---

### Post by zerhacke on 2009-09-09
Noa, a shell script is not a program.  This person has repeatedly said program and you keep giving them shell scripting advice.

---

### Post by NoaHall on 2009-09-09
Yeah, sorry, I got it after I finished writing.. Sorry. 

First, I think you should get Glade.
sudo apt-get install glade

Have a play with that. Come back to us if you need any help. It should get you started, and then from there, you could start doing it from just gedit.

PS, sorry for getting confused - my brain leaps into the terminal before the GUI.

---

### Post by Pirolocito on 2009-09-09
> **megane16v said:**
> Let's try this way...

I'm new to Unix
I WANT to learn more of it.

Where is my problem?

I'm stuck with Xlib and X11

How do i make simple "hello world"program using X11?

I've seen examples on internet,but where do I make that example(in text editor,terminal?) and how can i see results of my programming? Thanks,hope u would help,because i don't know who will if you can't!

I know what you want, i and have the answer! try GAMBAS

sudo apt-get install gambas2

or find gambas2 in synaptic package manager.

It's very similar to visual basic and easy to program and all visual thinks. It is possible to make packages to distribute the code.

In this image there is a program i'm doing to do some Ventilation ducts calculations. It is very draft yet...

[IMG]http://img197.imageshack.us/img197/5720/abacus.png[/IMG]

Best regards

---

### Post by megane16v on 2009-09-09
Pirolocito,i have installed both Gedit and Gambas2,but Gumbas is sort of Visual Basic programming,I'm looking for C or at least C++ development interface. I was googling and found this [http://www.sai.msu.su/sal/F/5/](http://www.sai.msu.su/sal/F/5/) 
Maybe this would help?

---

