---
title: "Applications and the Terminal"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by cokaznsyco72 on 2011-04-21
I don't know how to deal with applications in the terminal. 

Open Office Draw froze up on me, and I was trying to figure out how to make it force quit. I couldn't figure out how to access it from the terminal to terminate it. 

So I guess I have two questions: 
How do I launch/terminate applications using the Terminal? 
Is there an analogue to the task manager of Windows in Ubuntu?

---

### Post by yetiman64 on 2011-04-21
> **cokaznsyco72 said:**
> I don't know how to deal with applications in the terminal. 

Open Office Draw froze up on me, and I was trying to figure out how to make it force quit. I couldn't figure out how to access it from the terminal to terminate it. 

So I guess I have two questions: 
How do I launch/terminate applications using the Terminal? 
Is there an analogue to the task manager of Windows in Ubuntu?

To kill a frozen application, use the key combination ALT + F2, type in xkill. Your cursor will change to an x, place it on the application and click. 

To kill an application using the terminal type in ```
killall -15 <application-name>
```but please note if multiple instances of the application are running they will all be killed.

To launch an application in terminal just type in its process name and hit enter eg to start openoffice draw use ```
ooffice -draw
``` note that when opening a program with terminal, if you shut the terminal down you will shut the program down as well.

Task manager equivalent is System > Administration > System Monitor > Processes Tab. Right clicking on a application name gives you the options to Stop, Continue, End or Kill a process.

Edit: just noted your join date, Welcome to the forums.

---

### Post by enarsee on 2011-04-21
Easier way,

Right click on the panel, add applet and add "Force Quit"

Whenever any application hangs, just click on the Force Quit Icon on the panel :D

---

### Post by cokaznsyco72 on 2011-04-21
Thanks for your help and for welcoming me. I just switched from windows. I've never used linux before, but I have used unix for some classes. 

@ yetiman
Is there a list or something of process names that I can refer to? 
I can't get the killall function to work. Here's what I'm typing: 

killall -I ooffice -draw

then I get back a list of options for killall. Is the terminal seeing -draw as an option that doesn't exist? 


@ enarsee
That was actually the first thing I tried. It closed the ooffice window, but there were still some ooffice processes running in the background that I couldn't figure out how to terminate. They , andwere keeping me from reopening the program, and I eventually had to restart. 


Well, thanks again for your help.

---

### Post by Hippytaff on 2011-04-21
if you find the process ID's of the processes you can do
```
 pkill PID
``` where PID is the process number. You can find this by either doing```
top
``` and looking for the processes and noting the ID's (also htop, but you might need to install htop) or doing```
pidof *Appname*
``` where appname is the name of the app (ie ooffice) this will return the PID.

---

### Post by Blasphemist on 2011-04-21
> **cokaznsyco72 said:**
> I don't know how to deal with applications in the terminal. 

Open Office Draw froze up on me, and I was trying to figure out how to make it force quit. I couldn't figure out how to access it from the terminal to terminate it. 

So I guess I have two questions: 
How do I launch/terminate applications using the Terminal? 
Is there an analogue to the task manager of Windows in Ubuntu?

I'd like to add here that for people not very familiar with using the terminal, CLI Companion can be a good tool. [http://okiebuntu.homelinux.com/okwiki/clicompanion](http://okiebuntu.homelinux.com/okwiki/clicompanion)

It does not have all commands in it but the link above includes showing how to add commands. To me, if you use it and add commands when you learn them here in the forums, they will be there the next time you want them. Commands show the syntax, user input and description. You can also find the command in the list, right click and choose apply and it will either run or if user input is needed prompt you for that input.

---

### Post by yetiman64 on 2011-04-21
> **cokaznsyco72 said:**
> Thanks for your help and for welcoming me. I just switched from windows. I've never used linux before, but I have used unix for some classes. 

@ yetiman
Is there a list or something of process names that I can refer to? 
I can't get the killall function to work. Here's what I'm typing: 

killall -I ooffice -draw

then I get back a list of options for killall. Is the terminal seeing -draw as an option that doesn't exist? 


@ enarsee
That was actually the first thing I tried. It closed the ooffice window, but there were still some ooffice processes running in the background that I couldn't figure out how to terminate. They , andwere keeping me from reopening the program, and I eventually had to restart. 


Well, thanks again for your help.

With openoffice, the command ooffice -draw only is to start it (I found this by checking the properties of its menu entry. Right click the Applications menu on the top panel and choose edit menus to get the window in the first attachment below, then highlight Draw and click properties). 

With it running go to System > Administration > System Monitor > Processes Tab and scroll down. It shows in the list as soffice.bin, so the command becomes
```
killall -15 soffice.bin
```**Edit:** you can actually just right click the line for soffice in System Monitor and select kill (see the 3rd attachment below).

I think that openoffice is probably the most difficult example for a new starter to come across for what you have asked. Previously even I would have used the same name with killall as what was used to start the app in terminal. The command to launch a program is found in its menu entry properties and the name to use with killall can be found in System Monitor. See the second attachment below.

The example in use is unfortunate and I hope this hasn't confused you too much.
[B]
Edit continued:[/B]
To do it fully in terminal use ```
ps -A
``` (This lists names and PIDs -process IDs) find the name for use with killall or the PID to use with kill

eg to kill it without using system monitor use in terminal use ps -A, find the name and PID number.

```
kill -15 <PID>
``` where <PID> is the number beside the process name in terminal

OR 
```
killall -15 soffice.bin
```

---

### Post by cokaznsyco72 on 2011-04-25
Thanks for the help. It's taking me a while to get through all this info, because I'm pretty busy with school.

---

### Post by conradin on 2011-04-25
"system monitor" is a panel applet with will give you a gui of running processes, and other system properties, it is akin to the windows task manager.

Right click the panel and select add to panel then type system monitor.

---

### Post by deconstrained on 2011-04-25
> **Hippytaff said:**
> if you find the process ID's of the processes you can do
```
 pkill PID
``` where PID is the process number.
Actually, pkill will search for the program by name and kill it. You don't have to feed it a PID--in fact, that's not how the program is meant to be used;
[quote=man pgrep,pkill]look up or signal processes based on name and other attributes[/quote]

---

### Post by collisionystm on 2011-04-25
> **cokaznsyco72 said:**
> I don't know how to deal with applications in the terminal. 

Open Office Draw froze up on me, and I was trying to figure out how to make it force quit. I couldn't figure out how to access it from the terminal to terminate it. 

So I guess I have two questions: 
How do I launch/terminate applications using the Terminal? 
Is there an analogue to the task manager of Windows in Ubuntu?

Add force quit to a panel. It will save your ***.

Open terminal

Search for your running app with

ps aux | grep appname

When you grep you just type a partial of the name. It returns all relevant results.

 pid real.name.of.app.that.you.got.from.previous.command

kill -9 pid.number.of.app.from.pid.command

If you want a terminal based system monitor, just type
```

top

```

---

