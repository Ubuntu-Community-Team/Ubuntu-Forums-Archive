---
title: "How to start several programs with one click?"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by kramer65 on 2010-05-04
Hello,

I installed some programs on my pc which I have to start to get my MIDI-keyboard working (Jack, Patchage, ZynAddSubFX, Ardour etc.). Since I don't want to click through the menu's about 3 times for every program to start, I wonder if it is possible to start a set of programs with a single click?

Does anybody know how I would be able to do this?

---

### Post by VeeDubb on 2010-05-04
The easiest way would be to create a simple shell script to launch them.

The only thing you will have a little (and I mean little) bit of trouble with, is getting them to all launch at the same time.  By default, the second line of a shell script won't execute until the first line is done executing.

For example, if you created a script to launch open office and firefox, firefox wouldn't launch until you closed Open Office.

I know there are several different ways to accomplish executing them all at once, but it's 3am here, and I just got off a wicked long shift, so I can't think of them at the moment.

---

### Post by r-senior on 2010-05-04
Have you tried System - Preferences - Startup Applications - Options - Remember Currently Running Applications after you've done the three clicks but before you start anything else?

Alternatively you could add them as Startup Applications using the same program? But then you'd need to work out the terminal commands and options. In that case, you could combine the three into a single bash script and invoke that as a startup application:

```

#!/bin/bash

myfirstapp &
mysecondapp &
mythirdapp &

```

Save as $HOME/bin/mystartup and add that as a startup application?

---

### Post by kramer65 on 2010-05-04
Haha, thanks for responding anyways.. :) Sleep well!

Anybody else know how I would have them launched all at once..?

---

### Post by kramer65 on 2010-05-04
The thing is that I do not want to start them at startup. I want to start them when I want to, but using only one click..

---

### Post by zeroseven0183 on 2010-05-04
You can use the same script that r-senior mentioned
1. save it somewhere in your /home directory (something like "start_program1_program2_program3.sh")
2. right-click on the file and select Properties
3. check the box to "Allow executing it as a program"
4. Once you have that, you can now add it to the Menu or create a Launcher for it on your panel

---

### Post by r-senior on 2010-05-04
The little script idea should work (just tried it with calculator and gedit), but you'd add it to your menu or as a panel shortcut.

You also need to 

$ chmod +x $HOME/bin/myscript

Give it a try and see how far you get?

EDIT: The chmod does the same as zszoet's "Allow executing as a program", but zszoet's is easier. ;)

---

### Post by 3rdalbum on 2010-05-04
I answered this question literally a couple of hours ago.

r-senior has the answer. You do indeed create a shell script. You make it executable (right-click it, go to Properties then to Permissions, and then click the checkbox to make it executable). Then you right-click your panel or the Desktop and create a custom application launcher. Click the Browse button and choose the shell script.

Then with a single click on your new panel icon, or a double-click on a desktop icon, you'll have programs started simultaneously.

---

### Post by kramer65 on 2010-05-04
Hi Guys, sorry for not answering. Something came up and I was unexpectedly away from my pc for a little while. I just fixed it and it works like a charm!

Thank you guys so much!

---

### Post by cgroza on 2010-05-04
Please mark the thread as Solved...

---

