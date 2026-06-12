---
title: "Questions about executing commands"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by scared0o0rabbit on 2009-09-02
I apologize if this is in the wrong section.  I'm a beginner, and I figured this would be a good starting point.

I've been using for all of about 4 hours now, I stumbled my way through getting code::blocks installed.  I've used code::blocks a little bit on windows and liked it, so I wanted to stick with the same IDE when I tried linux.

The problem I'm running into is that my code when compiled in codeblocks works just fine after being compiled, but only if I hit the run button within codeblocks.  If I try and browse to the console application I wrote and double click it in nautilus, it doesn't appear to do anything (though when I check the system monitor it is running and it's flooring my cpu).  If I try and work my way there through the terminal and run the application it just says something like command not found (I made sure I typed it with the same cases as the file is named).

So any suggestions on what gives?  This is for a c++ class I'm in, and I can certainly capture my output in windows and turn it in that way, but I'm really interested in learning more about linux.  Is there some step I'm missing somewhere?  I checked the permissions on the file and it said I have execute permission.  Should I try and compile a simple hello world program and see if that will run for me?  I find it strange that when the executable is run from within codeblocks it doesn't seem to have an issue working at all, but as soon as I try and do anything with it outside of codeblocks it just seems to fall apart on me.

Any pointers (and I don't mean the * type lol) would be greatly appreciated.

---

### Post by Chronon on 2009-09-02
The current directory isn't automatically in the path in Linux.  So, you have to do
```
./name_of_binary
```
instead of
```
name_of_binary
```
to run it from the terminal.

---

### Post by scared0o0rabbit on 2009-09-02
That did it.  Thanks!

So double clicking an executable in nautilus won't run it then?  Is there a way to run an executable that isn't in the applications list from the gui, or do I always have to open the terminal?

---

### Post by Gaweph on 2009-09-02
Doulbe clicking it will run it, which is why you were seeing it Running when you were looking at the system monitor.

The difference between this environment and windows in this case, is that in windows it will open up a console and show you your application running.  In ubuntu it wil not, it will just run.  If you ope na terminal and do ./appplication_Name then you will see the output because you ran it from a terminal.

If you think abotu it it makes sense not to show you, unless you do it from a terminal.  It means you can write apps, and get them to run in the background without being bothered.

If you ahd written an application with a GUI frontend then you would have seen it load the GUI.

Hope that explanation makes sense.

---

### Post by Gaweph on 2009-09-02
Also i forgot to mention, you can see any application running by starting it from teh console.

Try running: 

**gedit** 

from the console.

gedit will load, but you will also see all of its output in the console, its very handly for debugging your GUI's as well as your Console apps :)

---

### Post by scared0o0rabbit on 2009-09-02
That does make sense.  One last question on this topic then.  Is there a reason why it seems to floor my cpu when I run it outside of the terminal but not when it's run inside the terminal?

---

### Post by Gaweph on 2009-09-02
I really dont know.  Could be the difference in behavious when run inside the terminal.  Maybe when running outside then it does not have anything to do but to carry on, but inside it has to output itformation to the console.  Probably not.

If its a while(true) kind of app then try making the htread sleep for 5ms or something before each iteration.  Maybe it just isnt stopping when its running alone, but with the terminal it has to wait to output to something??

Again, i dont know.

---

### Post by scared0o0rabbit on 2009-09-02
Well it is a while app, it really should just be sitting there waiting for keyboard input from the user.

---

### Post by Gaweph on 2009-09-02
oh right, could be that then.  It aint going to get any input withoput a console.

---

