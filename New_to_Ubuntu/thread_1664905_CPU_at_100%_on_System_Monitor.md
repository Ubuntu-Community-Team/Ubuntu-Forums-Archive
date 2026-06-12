---
title: "CPU at 100% on System Monitor"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by Chris Edgell on 2011-01-11
I have installed Jaunty into this Celeron TM 1300MHz CPU that I acquired.  System status says that Available disk space is 28 GiB.  I have two old, small computers sitting right next to each other, both with Jaunty -- the one article I found on the subject says:

This issue can be caused by any of the below possibilities.

   1. Other programs being run in the background.
   2. Computer Trojan, Virus, Worm, Spyware or other malicious program.

Since I just installed this distro it doesn't seem like it could be caused by a malicious program.

When I see what is running it only says Gnome-system-monitor and that varies from 10% to over 40% -- but then as soon as I click back to the "Resources" tab the graph shows jumping right to 100% and stays there.

Who can explain this to me, or tell me why?  Thank you.

---

### Post by davidmohammed on 2011-01-11
system monitor is a little heavy weight (cpu usage)

suggest type

top

in a command window - what is the highest cpu usage process (first in the list)?

---

### Post by Chris Edgell on 2011-01-11
I'm very sorry David, but I have no idea what you mean.  Can you be more specific?  I appreciate the response though.

---

### Post by davidmohammed on 2011-01-11
choose Applications - Terminal

type in the window

top

this will display some statistics in the window.  Look at the %CPU column - what is the "COMMAND" that is the highest %CPU value.

---

### Post by Chris Edgell on 2011-01-11
Okay.  I got there.  

First command is XOrg - that varies from less than one % to 12 or so %.

Second is gnome-terminal less than 1% to around 3%

Now, on this site I see that my memory is almost full, I'm going to put another stick in there and see if being that close to swap is using up the usage.....

---

### Post by no2498 on 2011-01-12
htop tells you more and how to stop them
it comes up in system tools also
as for the memory 
ubuntu/linux uses it different than windows
you can free some up
in a terminal type free -m  click enter

---

### Post by Chris Edgell on 2011-01-12
Oh, I'm glad I happened to look at my threads...I didn't realize you'd posted here.  I think I entered what you said and this is what came:

chris@chris:~$ free-m
No command 'free-m' found, did you mean:
 Command 'freedm' from package 'freedm' (universe)
free-m: command not found
chris@chris:~$ freedm
The program 'freedm' is currently not installed.  You can install it by typing:
sudo apt-get install freedm
chris@chris:~$ sudo apt-get install freedm
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package freedm
chris@chris:~$

So I can only wonder what next...
Thank you for your input.

---

### Post by NightwishFan on 2011-01-13
What the 2nd poster meant was that the graph for the system monitor itself has high cpu overhead, and that is probably why it shows up as 100%. On an old machine that seems correct to me.

Also, you need to use correct formatting when using terminal commands. You forgot the space, for example:
```
free -m
```

Also, more RAM would not hurt, and it certainly more important than a good cpu in Ubuntu. Linux uses memory different from other systems, it goes by the philosophy that more used is better (and it is). So fuller ram is not a big deal unless you are actually slowing down.

Basically, if everything is at least somewhat fast, your machine is in good working order. Also note Jaunty is out of service release, it is still fine to use it, but it will not get upgrades. I am sure Lucid would run just as well and have 3 years of support. :)

---

### Post by Chris Edgell on 2011-01-13
chris@chris:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           236        228          8          0          8         90
-/+ buffers/cache:        129        107
Swap:          691         10        681
chris@chris:~$ 

Hi NightwishFan I remember you.

And me, I thought I was being so careful to put that space in...but here we have the output.

Thank you for your post,  Very good information.

Somehow, I have now got two threads on the same subject, we've got to drop one of them or someone will come and throw one out...or some kind of action can be taken.

---

### Post by NightwishFan on 2011-01-13
```
chris@chris:~$free -m
             total       used       free     shared    buffers     cached
Mem:           236        228          8          0          8         90
-/+ buffers/cache:        129        107
Swap:          691         10        681
chris@chris:~$
```

Looks a bit low ram for Xubuntu, but it seems to be in working order.

> Hi NightwishFan I remember you.

Likewise! How are you? :)

> Somehow, I have now got two threads on the same subject, we've got to drop one of them or someone will come and throw one out...or some kind of action can be taken.

Simply use the report post button in one of the threads and explain the situation, that will notify a mod. :)

---

