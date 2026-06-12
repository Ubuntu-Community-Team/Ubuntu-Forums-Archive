---
title: "Is there a ctrl-alt-del equivalent?"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by John Hale on 2009-01-18
Guys Is there a ctrl-alt-del equivalent? For when programs freeze and you want to shut the window down when the x won't work, at the moment I leave them there and they're gone when I reboot

Cheers

---

### Post by Shippou on 2009-01-18
Try SHIFT+BACKSPACE. The caveat: All of your programs will close. But then, it would kill X.

Or another thing: Try pressing the X Button many times while the application does not respond. A popup window will appear asking you if you want to force kill the application or not. Just kill the application.

---

### Post by binbash on 2009-01-18
ctrl + alt + backspace

---

### Post by redseventyseven on 2009-01-18
You mean like the Windows Task Manager, where you can terminate processes that have ceased to respond?

There's a similar dialog box available in the Session Manager (under the Current Session tab) where you can kill processes - you can also do it from the terminal if you know the name of the process using the killall command, e.g.

```
killall firefox
```

Either works fine.

---

### Post by jakupl on 2009-01-18
well I use the Force Quit Button on the panels. If you right click the panel, choose Add to Panel, and search for "force quit". Then you will have a clever little button you can press to kill any misbehaving application.

---

### Post by stderr on 2009-01-18
There are many, many equivalents :)

Firstly, there's system monitor. Alt+F2 and type gnome-system-monitor. When that's launched, click the Processes tab, and you should be in familiar territory.

You can also add that to the system bar, and have graphical representations of CPU usage, mem usage, network... etc. Also, then you just click once on that, and system monitor pops up. You can add that to the bar by right clicking, Add to Panel, scroll down and find System Monitor.

There are many, many other ways. Using a terminal: (Applications -> Accessories -> Terminal)

You can kill all instances of PROGRAM_NAME with: 

```
killall PROGRAM_NAME
```

So, kill all firefox windows with

```
killall firefox
```

You can kill specific programs too, but to do this you need to get it's process ID number (PID). You can find this in a number of ways:

```
pidof PROGRAM_NAME
```

e.g.

```
ace@ace1:~$ pidof rhythmbox
5371

```

Then you can kill it with kill:

```
kill 5371
```

You could even combine the two actions:

```
kill `pidof rhythmbox`
```

However, you might not know the full name of the program. In this case, use something like this:

```
ps aux | grep PART_OF_PROGRAM_NAME
```

e.g.

```
ace@ace1:~$ ps aux | grep evin
ace      31647  0.0  2.0 173236 72964 ?        Sl   Jan10   3:34 evince file:///tmp/uk-WHATEVER_FILENAME_MASKED-2006.pdf
```

That output tells us that the current PID of evince is 31647. So, we can kill that as usual:

```
kill 31647
```

The kill command by default sends a SIGTERM signal. This basically asks the program to close nicely, and lets it save any temporary data it needs to first. This is good - if it were, say, OpenOffice, it would have an opportunity to make backups of open unsaved files, etc, so hopefully you wouldn't lose any data.

However, SIGTERM isn't always sufficient. Sometimes you need to really kill a process forcefully. For this you use the SIGKILL signal, which is signal number 9. To really kill the evince process earlier, you'd use:  

```
kill -9 31647
```

It's always best to try kill (SIGTERM) first, and if that doesn't work, try kill -9 (SIGKILL).

If your whole graphical session is buggered, try Ctrl+Alt+Backspace to kill and restart the whole GUI (and all open applications!). You can also try switching to another TTY with Ctrl+Alt+F1, or Ctrl+Alt+F2,...F3...to F6. If that works and you get a console screen, login, and then you can find out what's screwing things up and kill it.

You can get a list of processes ordered by CPU usage (highest first) with the top command. Just type

```
top
``` 

and you'll get a list of processes and PIDs ordered by CPU usage. The PID is the leftmost number. The "%CPU" field is the percentage of CPU activity the process is using. So, if something's stuck on 100%-ish that shouldn't be, maybe that'd be a good process to try killing to regain control over your system.

You can quit the top screen (it continuously updates automatically) by pressing q.

Finally, if your system isn't responding to anything at all, you can still normally use the REISUB method to safely reboot.

This involves *holding down* Alt+PrintScreen all the time whilst pressing the following keys in order, with a second or so gap in-between each:

R  E  I  S  U  B

R tries to force the kernel to listen to your keyboard inputs
E sends SIGTERM to all processes
I sends SIGKILL to all processes
S syncs data to drives that's waiting to be synced
U remounts all drives as read-only
B reboots

The Alt+PrintScreen+{REISUB} method is a last resort - if you can't think of anything else but to press the power button, try it first.

HTH :)

---

### Post by mcduck on 2009-01-18
The closest equivalent for Task maanger in Windows would be the System Monitor, in System/Administration/System Monitor.

There isn't any keyboard shortcut to start it, but if you want you can create one:

With Compiz (the "desktop effects" enabled"):
1. open Compizconfig settings manager
2. Go to General options, Commands-tab
3. Under "Commands" set "Command line 0" to "gnome-system-monitor"
4. Under "Key bindings" set "Run Command 0" to whatever you want, like Ctrl-Alt-Del...

With Metacity (no "desktop effects"):
1. Open Configuration Editor (hit Alt-F2 and run "gconf-editor"
2. Set the key apps/metacity/keybinding_commands/command_1 to "gnome-system-monitor"
3. Set the key apps/metacity/global_keybindings/run_command_1 to "<Ctrl><Alt>Del"

After this pressing Ctrl-Alt-Del would pop up the System Monitor, which allows you to monitor and stop running programs just like you'd do in Windows.

---

### Post by Shippou on 2009-01-18
> **stderr said:**
> There are many, many equivalents :)

Firstly, there's system monitor. Alt+F2 and type gnome-system-monitor. When that's launched, click the Processes tab, and you should be in familiar territory.

You can also add that to the system bar, and have graphical representations of CPU usage, mem usage, network... etc. Also, then you just click once on that, and system monitor pops up. You can add that to the bar by right clicking, Add to Panel, scroll down and find System Monitor.

There are many, many other ways. Using a terminal: (Applications -> Accessories -> Terminal)

You can kill all instances of PROGRAM_NAME with: 

```
killall PROGRAM_NAME
```

So, kill all firefox windows with

```
killall firefox
```

You can kill specific programs too, but to do this you need to get it's process ID number (PID). You can find this in a number of ways:

```
pidof PROGRAM_NAME
```

e.g.

```
ace@ace1:~$ pidof rhythmbox
5371

```

Then you can kill it with kill:

```
kill 5371
```

You could even combine the two actions:

```
kill `pidof rhythmbox`
```

However, you might not know the full name of the program. In this case, use something like this:

```
ps aux | grep PART_OF_PROGRAM_NAME
```

e.g.

```
ace@ace1:~$ ps aux | grep evin
ace      31647  0.0  2.0 173236 72964 ?        Sl   Jan10   3:34 evince file:///tmp/uk-WHATEVER_FILENAME_MASKED-2006.pdf
```

That output tells us that the current PID of evince is 31647. So, we can kill that as usual:

```
kill 31647
```

The kill command by default sends a SIGTERM signal. This basically asks the program to close nicely, and lets it save any temporary data it needs to first. This is good - if it were, say, OpenOffice, it would have an opportunity to make backups of open unsaved files, etc, so hopefully you wouldn't lose any data.

However, SIGTERM isn't always sufficient. Sometimes you need to really kill a process forcefully. For this you use the SIGKILL signal, which is signal number 9. To really kill the evince process earlier, you'd use:  

```
kill -9 31647
```

It's always best to try kill (SIGTERM) first, and if that doesn't work, try kill -9 (SIGKILL).

If your whole graphical session is buggered, try Ctrl+Alt+Backspace to kill and restart the whole GUI (and all open applications!). You can also try switching to another TTY with Ctrl+Alt+F1, or Ctrl+Alt+F2,...F3...to F6. If that works and you get a console screen, login, and then you can find out what's screwing things up and kill it.

You can get a list of processes ordered by CPU usage (highest first) with the top command. Just type

```
top
``` 

and you'll get a list of processes and PIDs ordered by CPU usage. The PID is the leftmost number. The "%CPU" field is the percentage of CPU activity the process is using. So, if something's stuck on 100%-ish that shouldn't be, maybe that'd be a good process to try killing to regain control over your system.

You can quit the top screen (it continuously updates automatically) by pressing q.

Finally, if your system isn't responding to anything at all, you can still normally use the REISUB method to safely reboot.

This involves *holding down* Alt+PrintScreen all the time whilst pressing the following keys in order, with a second or so gap in-between each:

R  E  I  S  U  B

R tries to force the kernel to listen to your keyboard inputs
E sends SIGTERM to all processes
I sends SIGKILL to all processes
S syncs data to drives that's waiting to be synced
U remounts all drives as read-only
B reboots

The   method is a last resort - if you can't think of anything else but to press the power button, try it first.

HTH :)

Nice guide for a newbie. :)

IMO, the Alt+PrintScreen+{REISUB} is somewhat a joke timer. :)

---

### Post by stderr on 2009-01-18
> **Shippou said:**
> IMO, the Alt+PrintScreen+{REISUB} is somewhat a joke timer. :)

Huh? :) REISUB is one of those supremely useful things - when things do screw up, you want a way to ensure that nothing's being written to your drive at the point you power down! That's one of the things that always gets me about Winblows... once your system's screwed, there's no way out! You're literally forced to resort to a pot luck game of powering down, with no idea if any files will be corrupted as a result. And when it's NTLDR... ;)

I normally advise trying Alt+PrintScreen+R and then Ctrl+Alt+F1, Alt+PrintScreen+R and then Ctrl+Alt+Backspace... before the full REISUB. 

I suppose the biggest joke of REISUB is the name - "magic keys" \\:D/

---

### Post by caro on 2009-01-18
stderr, this has to be one of the most complete and well-explained answers ever posted on this forum!

---

### Post by earthpigg on 2009-01-18
... sticky this or make it the 'how-to' of the week or something, imo. that was epic, stderr.

---

### Post by stderr on 2009-01-18
Well thanks for the praise guys 'n gals. Maybe I should get out more :p

---

### Post by NotWindowsXPagain50 on 2009-11-09
There is a way to start system monitor with a shortcut

Step 1: Go to System, Preferences, Keyboard Shortcuts
Step 2: Scroll to a entry called Logging off and select it and press backspace
Step 3: Click Add, In the first box type in a name and in the second type [I]"/usr/bin/gnome-system-monitor"
[/I]Step 4: You're done
[I]
:D:D
[/I]

---

### Post by Jguy on 2009-11-09
I usually use Alt+F2, equivelent of the run command in windows. Even if you can't see it under the current application, it's still there. Type 'xkill' without quotes and it will turn the cursor into an 'X'. Click on the application that is unresponsive and it will instantly end it. Useful for anything that takes up the entire desktop where you can't get to a terminal and you don't want to switch to a full terminal (aka you have something important open)

---

### Post by JCK-longhair on 2009-11-10
> **NotWindowsXPagain50 said:**
> There is a way to start system monitor with a shortcut

Step 1: Go to System, Preferences, Keyboard Shortcuts
Step 2: Scroll to a entry called Logging off and select it and press backspace
Step 3: Click Add, In the first box type in a name and in the second type [I]"/usr/bin/gnome-system-monitor"
[/I]Step 4: You're done
[I]
:D:D
[/I]

I find this most useful, thanks!
But I remember in Windows that sometimes it was set up differently, so I'm used to using shift-ctrl-escape for Task Manager. I've now kept ctrl-alt-delete for Logging Off and set a new entry for System Monitor to use shift-ctrl-escape. ;)

---

### Post by Poodle Doodle on 2009-12-08
I READ ALL OF THE FOLLOWING and I thought -

Look I understand that your trying to be helpful - but don't you get it? 

When Firefox REALLY takes a Memory Leak - and the system is bogged down like FOREVER - the last thing I or anyone else needs is a course in astrophysics......

When Firefox is cache thrashing the computers guts out - and NOTHING else is either working or won't respond for like 5 or 10 minutes....

I just want something SIMPLE., like pull the plug from the power point, a big hammer on the CPU or a simple by rote FORCE HALT or FORCE KILL key combination.

That's why without going into all the issues, having a keyset that EVERYONE knows, like Ctrl + Alt + Del, is a wonderfully practical thing.




> **stderr said:**
> There are many, many equivalents :)

There are many, many other ways. Using a terminal: (Applications -> Accessories -> Terminal)

You can kill all instances of PROGRAM_NAME with: 

```
killall PROGRAM_NAME
```

So, kill all firefox windows with

```
killall firefox
```

You can kill specific programs too, but to do this you need to get it's process ID number (PID). You can find this in a number of ways:

```
pidof PROGRAM_NAME
```

e.g.

```
ace@ace1:~$ pidof rhythmbox
5371

```

Then you can kill it with kill:

```
kill 5371
```

You could even combine the two actions:

```
kill `pidof rhythmbox`
```

However, you might not know the full name of the program. In this case, use something like this:

```
ps aux | grep PART_OF_PROGRAM_NAME
```

e.g.

```
ace@ace1:~$ ps aux | grep evin
ace      31647  0.0  2.0 173236 72964 ?        Sl   Jan10   3:34 evince file:///tmp/uk-WHATEVER_FILENAME_MASKED-2006.pdf
```

That output tells us that the current PID of evince is 31647. So, we can kill that as usual:

```
kill 31647
```

The kill command by default sends a SIGTERM signal. This basically asks the program to close nicely, and lets it save any temporary data it needs to first. This is good - if it were, say, OpenOffice, it would have an opportunity to make backups of open unsaved files, etc, so hopefully you wouldn't lose any data.

However, SIGTERM isn't always sufficient. Sometimes you need to really kill a process forcefully. For this you use the SIGKILL signal, which is signal number 9. To really kill the evince process earlier, you'd use:  

```
kill -9 31647
```

It's always best to try kill (SIGTERM) first, and if that doesn't work, try kill -9 (SIGKILL).

If your whole graphical session is buggered, try Ctrl+Alt+Backspace to kill and restart the whole GUI (and all open applications!). You can also try switching to another TTY with Ctrl+Alt+F1, or Ctrl+Alt+F2,...F3...to F6. If that works and you get a console screen, login, and then you can find out what's screwing things up and kill it.

You can get a list of processes ordered by CPU usage (highest first) with the top command. Just type

```
top
``` 

and you'll get a list of processes and PIDs ordered by CPU usage. The PID is the leftmost number. The "%CPU" field is the percentage of CPU activity the process is using. So, if something's stuck on 100%-ish that shouldn't be, maybe that'd be a good process to try killing to regain control over your system.

You can quit the top screen (it continuously updates automatically) by pressing q.

Finally, if your system isn't responding to anything at all, you can still normally use the REISUB method to safely reboot.

This involves *holding down* Alt+PrintScreen all the time whilst pressing the following keys in order, with a second or so gap in-between each:

R  E  I  S  U  B

R tries to force the kernel to listen to your keyboard inputs
E sends SIGTERM to all processes
I sends SIGKILL to all processes
S syncs data to drives that's waiting to be synced
U remounts all drives as read-only
B reboots

The Alt+PrintScreen+{REISUB} method is a last resort - if you can't think of anything else but to press the power button, try it first.

HTH :)

---

### Post by hobo14 on 2009-12-09
> **Poodle Doodle said:**
> I READ ALL OF THE FOLLOWING and I thought -

Look I understand that your trying to be helpful - but don't you get it? 

When Firefox REALLY takes a Memory Leak - and the system is bogged down like FOREVER - the last thing I or anyone else needs is a course in astrophysics......

When Firefox is cache thrashing the computers guts out - and NOTHING else is either working or won't respond for like 5 or 10 minutes....

I just want something SIMPLE., like pull the plug from the power point, a big hammer on the CPU or a simple by rote FORCE HALT or FORCE KILL key combination.

That's why without going into all the issues, having a keyset that EVERYONE knows, like Ctrl + Alt + Del, is a wonderfully practical thing.

**Right Alt + Print Screen + K**

That's your simple hammer, and it's all you ever need to know.

---

### Post by xpod on 2009-12-09
> **Poodle Doodle said:**
> I READ ALL OF THE FOLLOWING and I thought -

Look I understand that your trying to be helpful - but don't you get it? 

When Firefox REALLY takes a Memory Leak - and the system is bogged down like FOREVER - the last thing I or anyone else needs is a course in astrophysics......

When Firefox is cache thrashing the computers guts out - and NOTHING else is either working or won't respond for like 5 or 10 minutes....

I just want something SIMPLE., like pull the plug from the power point, a big hammer on the CPU or a simple by rote FORCE HALT or FORCE KILL key combination.

That's why without going into all the issues, having a keyset that EVERYONE knows, like Ctrl + Alt + Del, is a wonderfully practical thing.

What could be simpler than adding the "force quit" utility to your panel as already mentioned or indeed using the key combo mentioned in the previous post?

> **hobo14 said:**
> **Right Alt + Print Screen + K**

That's your simple hammer, and it's all you ever need to know.

It seems i`ve been doing it wrong, i`ve been using the left ALT key;)

---

### Post by SteveNorman on 2009-12-09
Poodle Doodle, that quick fix mentality will cause you many many many problems later. Do it the correct way and fix the problem so you dont have to fix more things later.

Normally Force-quit will work and its easier than cntrl-alt-del. But unlike windows, you have more options if that doesnt work.How many times have you hit cntrl-alt-del and nothing happens? With my Wind0s experience that was pretty often. stderr's post was a thorough rundown of the steps to fix a worst case scenario. A proceedure for stopping and fixing things that dont work, instead of just throwing rocks at it and hoping it wont happen again. In windows, if control alt del doesnt work you hold down the reset key, which is a roll of the dice that your system will re-boot properly without losing data. If you pull the plug in any OS your risking a lot.

You would do well to not be lazy with your computer, be patient and learn some basic linux, learn how powerful good technique is and move beyond mcdonalds super-size solutions that kill your operating system in the long run.

Ubuntu is a great operating system, and its about 100x easier than most distros, and about 50x easier than it was a few years ago. Its about as simple as linux can get. 

BTW learn how to do hot keys and you can make cntrl-alt-del do anything you want, like play a wav file of fart noises through VLC while the optical trays go in and out. Or you can set it to reboot your crap after sending a log file to the King of Ireland. Or Both! Try that in windows or Mac.

---

### Post by Cuco3 on 2009-12-09
Great post stderr and others who contributed.

And watchout for that RIGHT ALT + PRINTSCREEN + K command. Make sure you don't have any important data open if you experiment with what it does!

---

### Post by Rave Gloves on 2009-12-09
If my program stops responding i would 
```
Alt+F2
```

then type xkill and click the program i want killed.

---

