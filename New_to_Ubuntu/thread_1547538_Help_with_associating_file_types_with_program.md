---
title: "Help with associating file types with program"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by Controls_Nut on 2010-08-06
After searching for a couple hours for solutions to my problem I'm beginning to have a deep rooted hatred for file type associations. Here is what I need to do:

1.) Associate python file types (.py or .pyw) with python so that I can double click on them and execute them immediately.

2.) Add komodo edit to the 'Open With' right click menu for python file types so I can edit my python files quickly.

Running: lubuntu 10.04, pcmanfm 0.9.5

PLEASE, no 'open with' click the 'Set selected application...' checkbox solutions. If that worked I wouldn't be posting. I would really like to have a command line solution that just plain WORKS, regardless of linux distro, application, or file type.

I've tried to edit the mimeapps.list file to no avail, probably because I don't know how. In pcmanfm I tried to use the 'custom command line' option by entering 'python %f' in the 'command line to execute' entry box. This edited the mimeapps.list file and created a python configuration file in the same folder. It also gave me 'python' as an open with option on the right click menu, which doesn't work.

Any help would be appreciated!

Thanks

---

### Post by TimEnid on 2010-08-06
right click on the file, choose properties, go to the Open With tab and choose the app. this is different than the method you described. you never have to select the app again. it will always open with what you select. this was a problem for me as well.

---

### Post by WelshChris on 2010-08-06
As TimEnid said:

1. Right click on .py file in nautilus, -> properties -> open with.
   Click on python, if it's in the list, else add the command, or even create one, if it's not there.  You just need "python", without quotes, no f% or anything else.
   If you need python to run in a terminal, use the custom command gnome-terminal -command="python %f"

2. Not sure about Komodo Edit.  Don't use it, and can't be bothered at two in the morning to build it! =)
Is it any good?

---

### Post by Controls_Nut on 2010-08-06
I should have clarified the 'Please no open with' solutions, properties>>open with>> solutions, or gui solutions in general. They don't work because half the time the application isn't in the list to begin with, nor is the 'browse for application' working. If you can tell me how to add python to the program list, I would be happy to do it this way.

@WelshChris

Thanks for the solution, I'll try it. I'm still interested in a command line solution though, something less dependent on which file manager you are using.

Komodo Edit is free software for editing python, perl, php etc... and is available for windows, mac, and linux. I suppose it depends on your tastes to answer 'is it any good', but I love it for working on python. Has simple but nice features like file comparison, syntax coloring/checking, autocomplete and calltips.

---

### Post by Controls_Nut on 2010-08-06
Nope, didn't work. Haven't seen a single solution yet that works. No 'open with' solution WILL work, because python is not showing up in any GUI list. Using just 'python' as the custom open command didn't work either, nice tip though.

Okay... new question, I'm guessing changing file associations is a function of the file manager itself, and is highly dependent on the file manager. So, since pcmanfm will only let me select programs from the start menu, how do I add python (and komodo edit) to the start menu? It would also be nice if they can be put under the menu selection >start menu>>programming>> which doesn't exist yet on my machine (no programming section under the start menu). 

If that doesn't work... what file manager do you suggest and how would I go about setting it as the default file manager?

Edit:

I'm crossing my fingers hoping this will also allow me to double click on my python files and have them run. I have a graphical python app which I'm sick of starting via command line, I have done/tried the following to make it 'double-clickable':

chmod +x main.py

and adding the following to the top of the python file:
#!usr/bin/env python      and I've tried:
#!usr/bin/env python2.6

neither works.

---

### Post by Controls_Nut on 2010-08-07
SOLVED:

Not really, lubuntu must obviously be rather immature as of yet... I installed the xubuntu desktop manager and it rocks!!! Got everything I needed setup in 5 minutes. Awesome. Maybe not as fast as lubuntu, but the convenience is worth it.

FTR:

Even the online python documentation suggests changing python files to executables:

chmod -x file.py
or 'mark as executable' or 'allow to run as program' etc... 

...It didn't work for me. Just make sure python is the default program for running python files and it is A-OK.

---

### Post by WelshChris on 2010-08-07
Probably down to the file manager you use!

I'm using default ubuntu - nautilus I presume is the file manager, and I managed to get both command-line python scripts and GUI based python scripts running using the methods I used before.

Glad you solved it though. =)

---

