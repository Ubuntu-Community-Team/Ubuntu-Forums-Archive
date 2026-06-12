---
title: "Shut Down Frozen Program?"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by BruisedQuasar07 on 2009-02-23
Is there a sequence of keys that will shut down a frozen program? Specifically, Firefox freezes on me sometimes (in Ubuntu 8.10). When this happens I get no response from clicking on "file" or "X". I know about hot rebooting the shell & hot rebooting Ubuntu. I figure there must be a key sequence that will shut down any frozen program. Is there?

--Bruised

---

### Post by mkvnmtr on 2009-02-23
Usually clicking on the X a couple of times gives me the option to kill the program. I have also added a kill icon to the panel. If I click the icon and then in the center of the window it will kill the program. It seems to me that when firefox freezes it is using so many resourses that I can't get a terminal open.

---

### Post by lykwydchykyn on 2009-02-23
Used to be ctrl-alt-esc would turn the cursor into an "x" which would kill any program you clicked on.  GNOME and/or Compiz might have changed this, though.  The program that is run by that sequence is called "xkill", so presumably you can assign that to another key combo or just alt-f2 and type it in.

---

### Post by binbash on 2009-02-23
pkill firefox 
OR

ps aux | grep firefox

then kill the pid : 

example : kill 111234

---

### Post by ChildOfMana on 2009-02-23
To do it graphically open a Terminal (Applications > Accessories > Terminal) and type;

```
xkill
```

This will change your mouse cursor to an X. Now click in the center of the program window you want to kill.

To do it via the command line you can use the *pidof* command, followed by the *kill* command.

```
pidof firefox
```

will give you the process ID of the program you want to kill (firefox, in this case). If the pid is 5960 (for example) you would then do;

```
sudo kill 5960
```

---

### Post by tea for one on 2009-02-23
Good evening

You can add to a panel the little application "Force a misbehaving application to quit"

Right click panel (upper or lower - it doesn't matter)
Select "add to panel"
Scroll down to "Force Quit"
Click "Add" icon

The little program works fine in Gnome.

---

### Post by BruisedQuasar07 on 2009-02-24
> **lykwydchykyn said:**
> Used to be ctrl-alt-esc would turn the cursor into an "x" which would kill any program you clicked on.  GNOME and/or Compiz might have changed this, though.  The program that is run by that sequence is called "xkill", so presumably you can assign that to another key combo or just alt-f2 and type it in.

Thank you. You are correct. ctrl - alt - esc doesn't work anymore but 
alt-f2 and type xkill is fast, simple, & works nicely.

--Bruised

---

### Post by sydbat on 2009-02-24
> **tea for one said:**
> Good evening

You can add to a panel the little application "Force a misbehaving application to quit"

Right click panel (upper or lower - it doesn't matter)
Select "add to panel"
Scroll down to "Force Quit"
Click "Add" icon

The little program works fine in Gnome.This is possibly the best little app for shutting down 'frozen' programs. I make sure to always add it after every install I do for people. The ironic thing is, I have it in my panel, but never have to use it...seems apps "just know" it's there and never misbehave...watch...now I'll be using it everyday... :p

---

### Post by BruisedQuasar07 on 2009-02-24
O.K. I tried it. Didn't know there is a panel drop down like that one. I've got the icon for "force quit" on my top panel now. That is a nice one click solution!

Thank you Tea for One & Sydbat

--Bruised :guitar:

---

### Post by maluka on 2010-04-24
"Force a misbehaving application to quit" is stuck on my screen after force quitting an application. How do I get rid of it?

---

### Post by _0R10N on 2010-04-24
When some program stop responding, or I'm trying to stop one, on a remote machine via ssh. I always choose
```
ps aux | grep <part_of_process_name>
```
to know the PID of the process, and then
```
kill <process_PID>
```
Sometimes that isn't enough, and you have to add a switch
```
kill -9 <process_PID>
```
to force the process to stop.

I know this is a solution already posted, but I want to empathize the fact that this is the best way, at least the best I know.


Kind regards!

_0R10N >>

---

### Post by ddecator on 2010-04-24
There is always the option of using killall, which I find to be easier than finding the pid of a process. This can be harder for obscure processes, but for things like Firefox it works great.

```
killall firefox
```

---

### Post by maluka on 2010-04-25
Thanks, I just restarted the machine to fix it.

---

### Post by utnubuuser on 2010-04-25
ps -A lists  all running process.

---

### Post by Drenriza on 2010-04-25
Only post #11 is a good reply.
 
Since he is the only one who has added
```
kill -9 PPID
```
 
The kill -9 is the strongest kill command you can send in an linux enviroment.
 
```
killall processname
```
```
kill PPID
```
 
is someworth good commands. But they only send a standard signal strenght of -15. And cant always kill a process that no longer responds.
 
To find a process that you wanna kill use the
```
ps -aux |grep processname
```
 
or if you want to find zombie processes
```
ps -el |grep -w Z
```
and then kill the processes by their PPID (Parent PID)

---

