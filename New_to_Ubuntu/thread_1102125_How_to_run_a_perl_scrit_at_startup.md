---
title: "How to run a perl scrit at startup?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-03-21
I am writting a little program in Perl and I'd like to have it launched in the terminal when I turn on my computer. I suppose I have to put it in the autostart apps, but I don't know what command to put so it launches. So far, I only get the terminal to start and then it just hangs. How should I go about it?

Thanks!

---

### Post by blueridgedog on 2009-03-22
There are two ways to start applications automatically that I am aware of.  One is to start them via the typically run command process, via commands in /etc/init.d/ (initialization directory).  A user would typically add their command to /etc/init.d/rc.local.  However, this would not have a graphical output inside your x server.

An alternative is to go to System - Preferences - Sessions and add your Perl script as a start up option for your session.  Click add then specify the path to your script.  The script should be fully debugged and working prior to integrating it into gnome.

Good luck.

---

### Post by ronocdh on 2009-03-22
> **blueridgedog said:**
> An alternative is to go to System - Preferences - Sessions and add your Perl script as a start up option for your session.  Click add then specify the path to your script.  The script should be fully debugged and working prior to integrating it into gnome.
I'd imagine this would work well enough for you, but are you comfortable with bash scripting? You could set a session script to launch a separate perl script, which sounds goofy, but you could comfortably execute things the way you're used to.

---

### Post by sylvainrb on 2009-03-22
@ronocdh I'm not totally sure I grasp what you mean but once I go to add my script to the startup sessions, what code should I put? I was thinking something like:
```
gnome-terminal perl ~/program.pl
```
But this doesn't work.

The perl script interacts with the user so that's why I want it to launch in a terminal. Thanks!

---

### Post by t0p on 2009-03-22
> **sylvainrb said:**
> @ronocdh I'm not totally sure I grasp what you mean but once I go to add my script to the startup sessions, what code should I put? I was thinking something like:
```
gnome-terminal perl ~/program.pl
```
But this doesn't work.

The perl script interacts with the user so that's why I want it to launch in a terminal. Thanks!

So what happens if you just put into the startup sessions:

```
perl /home/sylvainrb/program.pl
```

---

### Post by blueridgedog on 2009-03-22
> **sylvainrb said:**
> @ronocdh I'm not totally sure I grasp what you mean but once I go to add my script to the startup sessions, what code should I put? I was thinking something like:
```
gnome-terminal perl ~/program.pl
```
But this doesn't work.

The perl script interacts with the user so that's why I want it to launch in a terminal. Thanks!

I typically just include

```
#!/usr/bin/perl -w 
```

At the top of my perl scripts and then call them as shell scripts.

---

### Post by sylvainrb on 2009-03-22
@top I tried this and it executes it (I can see it in htop as it takes all my cpu) but it doesn't start in the terminal as I wish to.

@blueridgedog That is what I do and it works fine when I just call it, but I was just wondering if there was a way so it calls itself at startup.

---

### Post by fixitdude on 2009-03-23
gnome-terminal --help

says "--command=STRING" "Execute the argument to this option inside the terminal."

See the other options like that. You may have to use quotes or something.

I would think adding your command to the startup part of your session would work since you want X all up and working before you call it.


....
Vegas poker pay table tester perl script
[http://ubuntuforums.org/showthread.php?t=1103613](http://ubuntuforums.org/showthread.php?t=1103613)

---

### Post by Xiong Chiamiov on 2009-03-23
You don't want it running at startup, since X isn't running, and therefore gnome-terminal can't start.

Add to your ~/.bash_profile (create it if it doesn't exist):
```

gnome-terminal ~/program.pl

```
You might need to add an & to the end of that line.  Also, make sure that the gnome-terminal line works correctly when running it from your run dialog; I'm not sure of the syntax for starting a script in gnome-terminal.

---

### Post by sylvainrb on 2009-03-23
Thanks guys, I got it working! I used the command
```
gnome-terminal -e ./program.pl
```
I don't know why but I always look everywhere but the terminal help. I guess I'm not used to it yet.

---

