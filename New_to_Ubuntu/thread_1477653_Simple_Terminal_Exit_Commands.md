---
title: "Simple Terminal Exit Commands?"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by McRat on 2010-05-09
1)  When I do something like ***man ls*** at a command prompt, it lists the data, and says _Manual page ls(1) line 1/242 8%_ highlighted on the bottom of the screen.

How do I return to the command prompt?  I tried CNTL-C, Esc, etc.  What is normal way to terminate a command?  I can't find where it's documented.

2)  When I want to shut down the computer, what is the command line prompt to terminate?

Thanks for any assist.

---

### Post by SoFl W on 2010-05-09
It is the Vim editor, try   ":q"

[http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html)

---

### Post by Sealbhach on 2010-05-09
Press Q to get out of man pages.

One command to shut down the system is

```
sudo shutdown now
```or 

```
sudo halt 
```(it's a bit more harsh, I think, not preferred). 

.

---

### Post by McRat on 2010-05-09
Thanks!  q or Q was it.

Now for the shutdown.

---

### Post by McRat on 2010-05-09
***sudo shutdown now*** did this:

Terminated processes, etc, but dropped to a Blue ANSI screen called something like Boot Options, that included repair functions and such.  Top option was something like Restart From Root, so I clicked that, it started to initialize everything, but froze at Battery Management.

So like everything in life, one question leads to another.

How do I remove battery management (desktop server app), and is there other options for shutdown?

---

### Post by Sealbhach on 2010-05-09
Hi, there's a few other commands here:

[http://www.cyberciti.biz/faq/shutdown-ubuntu-linux-computer/](http://www.cyberciti.biz/faq/shutdown-ubuntu-linux-computer/)

and here

[http://ubuntuforums.org/showthread.php?t=137038](http://ubuntuforums.org/showthread.php?t=137038)


Do you want to uninstall battery management? You can do that in Synaptic Package Manager.

If you want to kill a process, there's a few ways of doing it. You can run "top", find out the process ID and run

pkill 12345

or whatever the number is. A more forceful way to kill a process is

kill -9 12345

Or install htop, that's a quicker way to kill processes you don't want.


.

---

### Post by McRat on 2010-05-09
Thanks!:)

---

### Post by utnubuuser on 2010-05-09
shutdown from terminal:> sudo shutdown -r  0for restart
-r = restart
0 =  in x number of seconds

---

### Post by SKhan on 2010-05-09
hello i am also a new user. and i was also unable to exit terminal with ctrl+C
what shortcuts i found to be working are as follow:

if terminal has white background then Ctrl+Shift+Q
if it's fullscreen terminal with black background then Ctrl+Alt+F7

Show full screen terminal = Ctrl+Alt+F1

---

### Post by zeekoman on 2010-05-09
To remove it this should work:
```
sudo apt-get remove battery management
```

To shutdown use shutdown..
```
sudo shutdown
```

---

### Post by zeekoman on 2010-05-09
@SKhan 
What do you mean "exit"? Are you running a GUI (Graphical User Interface_ or a CLI (Command Line Interface) system? If you're running a CLI system you can't exit the command-line because that is your system.. if your using a window-manager and have a GUI, use ```
startx
``` to start your window-manager etc. back up.

---

### Post by 3rdalbum on 2010-05-09
sudo halt

sudo reboot

First one shuts down the whole way, the second one reboots.

sudo pm-suspend

Suspends.

---

### Post by nikefalcon on 2010-05-09
> **McRat said:**
> ***sudo shutdown now*** did this:

Terminated processes, etc, but dropped to a Blue ANSI screen called something like Boot Options, that included repair functions and such. t.


the terminal equivalent for the shutdown from the GUI is: 
```

sudo shutdown -P now

```
this will power off your PC so that you can cut power to it.
there are lots of options you can try. Check the manual page.
```

man shutdown

```

---

