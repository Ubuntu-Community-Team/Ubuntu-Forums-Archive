---
title: "Redirecting gnome-terminal --command"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by balgaltz on 2010-06-09
Hi, I would like to redirect the output of a command in gnome-terminal
Here's what I have tried.

**Working - without gnome-terminal**
1. Tailing the file where the command is redirecting its stdout and stderr
```
tail -f mylogfile
```
2. Executing the command
```
ls -al > mylogfile 2>&1
```
These above works and I can see the tailing in the terminal and if I open that file.

**What I want, but not working**
1. Tailing the file where the command is redirecting its stdout and stderr
```
tail -f mylogfile
```
2. Executing the command in another gnome-terminal
```
gnome-terminal --command "ls -al > mylogfile 2>&1"
```
The tailing indicates that the output of the command is not redirected, stays blank.

Thanks in advance.

---

### Post by balgaltz on 2010-06-11
Bump

---

### Post by gmargo on 2010-06-11
Why?  What is the point of running gnome-terminal?

---

### Post by beckols on 2010-06-11
From where are you running this command?  Aren't you already in a gnome-terminal?  If not, are you running without X and/or Gnome started (because then you won't be able to run gnome-terminal)?

And yes, why do you need it to go through gnome-terminal?  I'm not sure exactly what you're trying to accomplish, maybe an explanation of that would elicit a clearer understanding.

---

### Post by yamex5 on 2011-03-07
Hello All, 

I cannot answer why Wister needs this functionality, but I can give you the reason I need it. I have inherited test scripts that output data indicating the health of of test. We have multiple devices running, 7 currently, and the tests need to be monitored periodically. 
I have come to the conclusion that a terminal can not be spawned, issued commands to run and have it stay up. Please let me know if that is incorrect if you can verify it. 

The overall idea for redirecting output to the gnome-terminal is this: 
1. Start off a master script to start the low level test script for each device. 
2. Spawn a terminal that lists the output of the test for each unit. 

Does anyone have any idea how to do it? :confused:
I am new to Linux and need to pick up a book soon. It seems that in the tradition of Unix, there should be a way to redirect the output from one process (the low level test script, in this case) to the spawned gnome-terminal. 

Thanks ahead of time to anyone with suggestions!  :-D

-Mike

---

