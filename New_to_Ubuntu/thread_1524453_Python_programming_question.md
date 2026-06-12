---
title: "Python programming question"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by paint4blood on 2010-07-05
Hello, I am brand new to Ubuntu and I am running version 10.04. I am trying to learn python (hence the reason for using linux [I know I can use it on windows but I want to add to the community]). I read a few articles on it but most of them say to open a text editor and put in the first line the location of python. The websites say to use 
#! /usr/local/bin/python

or

#! /usr/bin/python

[FONT=Verdana]My [/FONT]question is are these the default locations of python? Linux is brand new on my computer so nothing is chnage as far as file locations.
If these are the correct file locations then I just put one of the two as the very first line and it will work?
Also about saving my programs. I made a simple one and saved it but when I click on it it just opens up the text editor as is if it was just plain text and not a program.
How do it get it to run as a program and not a text document?
If I find the answer I will post it.
Thanks

---

### Post by paint4blood on 2010-07-05
The tut I talked about is based off of windows and in it the guy shows a icon on his desktop that when he clicks on it it runs the program. When I follow the video step by step only a text document shows and when I click on it all it does is open it like a text document (like I said). I hope I spelled out my problem as clear as you need it to be. Thanks again.

---

### Post by Marlonsm on 2010-07-05
To run a program the best way is to use the terminal, just open it, browse to the location (using the cd command) and run "python file-name.py"

---

### Post by 3rdalbum on 2010-07-05
Use /usr/bin/python, not /usr/local/bin/python.

Also, you need to make your Python script executable (Right-click, Properties, Permissions and "Allow this program to execute"), then to launch it you should drag it into the terminal window. When you double-click the script, now that it is executable, it should give you the option to run it or run in a terminal, but you'll find that it's better to run it in a terminal that's already open.

---

### Post by lukeiamyourfather on 2010-07-05
Python in Linux is slightly different than Python in Windows. The shebang (#!) at the beginning of the script tells the system what interpreter to use for the script. The Python in /usr/bin/python is the default Python installed on the system. The Python in /usr/local/bin/python is where Python could be if installed by the user from source, usually to get a newer version than what comes on the system.

In a terminal use the command "python" to open an interactive session or use "python /somewhere/script.py" to run a script (with or without the shebang). If you want to use the Python specified in the script with the shebang then just call the script itself in the terminal (/somewhere/script.py or use ./script.py if you're already in that directory). Cheers!

---

### Post by arsenic23 on 2010-07-05
If you use [COLOR="DarkRed"]**#!/usr/bin/env python**[/COLOR] it won't matter where python is installed, it should work regardless.  ( This is what I've been told anyway. )

---

### Post by Joeasaurus on 2010-07-05
Any one around that can confirm the /usr/bin/env thing? I wasn't aware of this and it seems a brilliant method.

---

### Post by Bachstelze on 2010-07-05
> **Joeasaurus said:**
> Any one around that can confirm the /usr/bin/env thing? I wasn't aware of this and it seems a brilliant method.

Yes, it works.

---

