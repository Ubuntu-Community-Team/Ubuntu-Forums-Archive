---
title: "gambas trouble"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by coletsou on 2010-01-04
hi!

i am new to gambas..i am using ver 2.7 and using beginner's guide manual..following all the instructions, i tried running a sample program but i cannot view the output on the console screen/window..what should i do?  please help.:P:confused:

thanks a lot..

---

### Post by kalaharix on 2010-01-04
Hi,

I don't know what you mean by 'on the console'.

Start a new project and name it. Double click on FMain in the project window on the left to display the form. Drag  a button (the picture says 'OK') from the toolbox (bottom right) onto the form. Double click on button1 to display FMain.class and type 'print "hello world"' (without single parentheses) directly under PUBLIC SUB Button1_Click().

Run the program by clicking the right arrow in the icon bar (or debug, run from menu) and then click the button. You will see Hello world in the console. If you compile this program and run it as a standalone you will not see this console.

You could, for example, add a label to the form. Click on FMain.form to display the form again. Drag a label (shows 'A' in the toolbox) from the toolbox to the form. It will have the default name label1. Under the 'print "hello world"' line add 'label1.text="hello world"' (without single parentheses) and run the program again. Click on the button.

Another way: the console example supplied with Gambas uses a textArea to simulate a console within the gui but I hope I have shown you how to get going.

If you are using the eBook by John Rittinghouse, bear in mind that it was written for Gambas 1.0 and is quite out of date. A google search should give you some more up to date tutorials.

rgds

---

### Post by coletsou on 2010-01-07
hi!

thanks a lot to your reply..what i meant with the "console" is the "output window". after running the program, the output window is blank..  what should i do?  please help..thanks..:confused:;)



coletsou

---

### Post by armeranda on 2010-01-07
after running the program, the output window is blank..  what should i do?Pls help me.
Thanks

---

### Post by kalaharix on 2010-01-07
hi,

give me details of the program you are running (i.e. a listing) and where you are getting it from.

rgds

---

### Post by coletsou on 2010-01-12
good day!

..below are the lines of program code i tried to run in Gambas IDE..

STATIC PUBLIC SUB Main()
   DIM N AS Integer
   DIM R AS Integer
   N = 3
   R = *6
   PRINT “===> “;N;" | ";R; " and "; *N ; " | "; *R;
END

..i am using Gambas ver 2.7 and Ubuntu ver 8.04
..i used the following project types:
     1.  Graphical Application
     2.  QT Graphical Application
     3.  GTK+ Graphical Application
..in project types 1 & 2, output window is blank, i cannot see the output
..in project type 3, error says "Some components are missing: gb.gtk.ext"

..please help..i know this is a very simple program yet i am having trouble..i believe that getting through this will open doors for me to continue using Gambas and learn more...

..thanks a lot as always...

sincerely,
coletsou

:confused::):p

---

### Post by kalaharix on 2010-01-12
Hi,

Gambas, like other object oriented languages, is event driven. Something must trigger the calculations. You have no trigger in your program. The example below is triggered by the form open event (i.e. when the form initially opens). You could just as easily use the click of a button to do the calculation by putting the code below in a button1_click() event (assuming you had put a button on the form).

I haven't a clue what calculations you are trying to print with your print command. I suggest you look at the available arithmetic operators ([http://gambasdoc.org/help/cat/arithop](http://gambasdoc.org/help/cat/arithop)).
> 

PUBLIC SUB Form_Open()
  DIM N AS Integer
  DIM R AS Integer

  N = 3
  R = 6

  PRINT "n times r = "; N * R
  PRINT "n divided by r = "; N / R
  PRINT "n to the power r = "; N ^ R
END



---

### Post by coletsou on 2010-01-13
good day!

.. at last, with your help i was able to run the program and view the output..
.. thank you very much..
.. 'hope i can still consult you if i encounter trouble again in my succeeding explorations with Gambas
.. till next time..

salamat..

:D:P:)

---

### Post by Narendran95 on 2010-11-02
Hey, I'm new to Gambas Too! I really Need help... I made an Infra-red based Touchscreen device (The position where you touch blocks the IR rays there from reaching their corresponding receivers). I also used Arduino to process this and send the data via Serial Port. But that's not the matter. I would really appreciate if you give me the code to :
1. Simulate Left Mouse Click
2. Keep the Left Mouse Button Down
3. Release Left Mouse Button

I already found the code to move the cursor to a position : Mouse.Move(x,y)

I'm gonna be using this on a ubuntu netbook edition as they have big menus and icons. (Easy to touch)

Thanks in advance...

---

### Post by kalaharix on 2010-11-03
Hi

Cool project. I would be interested to see details.

The available mouse events are defined by the object to which they apply. A button (for example) in Gambas has click, doubleclick, mousedown, mousemove, mousedrag, mouseup, mousewheel events while the form that it sits on has those minus the click event. As you press '_' after 'Public sub Form....', a help window appears showing you the available events for that object.

Use mousedown to set a flag and mouseup to release. That will tell you whether the mouse is pressed.

Referring to your button1_click() event from another class will 'simulate' a mouse click.

rgds

---

