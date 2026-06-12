---
title: "run .desktop in terminal"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by craq on 2009-09-07
I have created a shortcut to an application, ML.desktop, which runs as expected when double-clicked. I would like to run it from the terminal, but can't figure out how. I get the following error, which makes sense because the .desktop file doesn't have a shebang.

```
$ ./ML.desktop
./ML.desktop: line 1: [Desktop: command not found
./ML.desktop: line 16: X-DBUS-ServiceName=: command not found
./ML.desktop: line 17: X-DBUS-StartupType=none: command not found
./ML.desktop: line 18: X-DCOP-ServiceType=none: command not found
./ML.desktop: line 19: X-KDE-SubstituteUID=false: command not found
./ML.desktop: line 20: X-KDE-Username=: command not found
./ML.desktop: line 21: X-Ubuntu-Gettext-Domain=desktop_kdebase: command not found
```


My reason is that the .desktop file includes the 'Work path' variable, which I want to set at launch. 

Alternatively, 
a)how would I incorporate the workpath variable into a bash script that calls/links to the original application (on a network)?
b) how would I assign a keyboard shortcut to a .desktop file?

Don't know if it's relevant, but I have Jaunty and KDE4.2.2

---

### Post by Diabolis on 2009-09-29
Why don't you use a **alias**?

Edit **~/.bashrc**, at the end of it add any aliases, example:
```
alias myalias='applicationName arg0 arg1 arg2'
```
arg# are any arguments you want to pass to your program, the work path in this case.

*note: After editing the file, the new aliases will be picked up in the next new terminal.

---

### Post by nothingspecial on 2009-09-29
Is it that the application is on your desktop. In which case you need to be in /home/username/Desktop for that command to work.

If you put it in your path ie /home/username/bin/ (which doesnt exist untill you create it) or /usr/bin/ so that all users can use it then you just need to type ```
ML.desktop
```.

On the other hand I have no idea what this application is and have no experience with a .desktop app, so all of the above may well be nonsense.

Well it`s not, but it may not apply in this particular case. Enlighten me.
> **Diabolis said:**
> 

*note: After editing the file, the new aliases will be picked up in the next new terminal.

Or you can just type ```
bash
``` to restart bash - but you will loose your history from the moment you opened that terminal - y`know, that thing where you press the up arrow and it tells you what you just typed.

I don`t think I`m quite "on the ball today" :-\"

---

### Post by juancarlospaco on 2009-09-29
Edit the launcher, and add.

**xterm -e "commandyouwanttorun"**

it opens automaticaly a terminal, and run the command inside

---

### Post by Darkwing-Duck on 2009-09-29
Either move it the /home/username/ folder or, create a small script to run it in the /home/username/ folder.
 
Open a text editor and put the full path to what you are trying to run.
 
Save it in the /home/username/ folder.
 
chmod it to execute.
 
```
sudo chmod +x /home/username/filestochmod
```
 
Then when you open terminal it will be right there to bash it with ./runme
 
Hope this helps a bit.

---

